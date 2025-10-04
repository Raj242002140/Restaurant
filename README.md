# Restaurant
#include <iostream>
using namespace std;
struct restaurant
{
	int no;
	string food_name;
	float amount_of_food_quantities;
	int price;
}

menu[1000];
struct food
{
	string food_name;
	int food_price;
} food[1000];
void ac()
{
	food[1].food_name="Fried chicken";
	food[1].food_price=1*575;

	food[2].food_name="Sizzling chicken";
	food[2].food_price=1*655;

	food[3].food_name="Mongoliam chicken";
	food[3].food_price=1*565;

	food[4].food_name="Grand Mughal Spaecial Kind Kong";
	food[4].food_price=1*390;

	food[5].food_name="Mixed Vegetable with Chicken and Prown";
	food[5].food_price=475;

	food[6].food_name="Thai vegetable";
	food[6].food_price=435;

	food[7].food_name="prown chilli";
	food[7].food_price=627;

	food[8].food_name="Spaghetti Bolognese pasta";
	food[8].food_price=600;

	food[9].food_name="Chicken burger";
	food[9].food_price=300;

	food[10].food_name="Fish burger";
	food[10].food_price=250;

	food[11].food_name="Chicken chilli onion";
	food[11].food_price=525;
}
int n=0;
int total_amount_money=0;
int total=0;


void food_information()
{
	int menu_food_item_number;

	do
	{
		n++;
		cout<<"enter the food item number:";
		cin>>menu_food_item_number;
		if(menu_food_item_number<12)
		{
			menu[n].no=n;
			menu[n].food_name=food[menu_food_item_number].food_name;
			cout<<"enter amount of food quantities: ";
			cin>> menu[n].amount_of_food_quantities;
			menu[n].price=menu[n].amount_of_food_quantities*food[menu_food_item_number].food_price;
			total_amount_money=total_amount_money+ menu[n].price;
			total=total+ menu[n].price;
		}
	}
	while(0<menu_food_item_number&&menu_food_item_number<12);

}

void print()
{
	cout<<"NO\t"<<"Food name";
	for(int i=0; i<4; i++)
	{
		cout<<"\t";
	}
	cout<<"Amount of food quantities\t"<<"Food price\t"<<"Total amount money\n";
	for(int i=1; i<n; i++)
	{
		int len = menu[i].food_name.size();
		cout<<menu[i].no<<"\t"<<menu[i].food_name;
		for(int j=0; j<(42-len); j++)
		{
			cout<<" ";
		}
		cout<<menu[i].amount_of_food_quantities;
		for(int i=0; i<4; i++)
		{
			cout<<"\t";
		}
		cout<<menu[i].price<<"\t\t";
		if(i==n-1)
		{
			cout<<total_amount_money<<"\n";
		}
		else {
			cout<<"\n";
		}
	}
}

void chang_food_item()
{
	int changs_food_item_number;
	cout<<"enter the changs food item number of this your order list: ";
	cin>>changs_food_item_number;
	for(int i=1; i<=changs_food_item_number; i++)
	{
		if(i==changs_food_item_number)
		{
			int chang_of_topice;
			cout<<"1.Chang the amount of this food quantities.\n";
			cout<<"2.chang the food item.\n";
			cout<<"enter chang of topice: ";
			cin>>chang_of_topice;
			if(chang_of_topice==1)
			{
				total_amount_money=total_amount_money- menu[i].price;
				total=total-menu[i].price;
				int changs_amount_food_quantities;
				cout<<"enter changs amount of food quantities:";
				cin>>changs_amount_food_quantities;
				menu[i].amount_of_food_quantities=changs_amount_food_quantities;

				int menu_food_item_number;
				cout<<"enter the food item number:";
				cin>>menu_food_item_number;
				menu[i].price=changs_amount_food_quantities*food[menu_food_item_number].food_price;
				total_amount_money=total_amount_money+ menu[i].price;
				total=total+ menu[i].price;
			}

			else if(chang_of_topice==2)
			{
				total_amount_money=total_amount_money- menu[i].price;
				total=total-menu[i].price;
				int menu_food_item_number;
				cout<<"enter the food item number:";
				cin>>menu_food_item_number;

				menu[i].food_name=food[menu_food_item_number].food_name;
				cout<<"enter amount of food quantities: ";
				cin>> menu[i].amount_of_food_quantities;
				menu[i].price=menu[i].amount_of_food_quantities*food[menu_food_item_number].food_price;
				total_amount_money=total_amount_money+ menu[n].price;
				total=total+ menu[i].price;

			}
		}

	}
	print();

}

void delete_food_item()
{
	int delete_food_item_number;
	cout<<"enter the delete food item number of your Order list: ";
	cin>>delete_food_item_number;
	for(int i=1; i<n; i++)
	{
		if(i==delete_food_item_number)
		{
			total_amount_money=total_amount_money- menu[i].price;
			total=total-menu[i].price;

			for(int j=delete_food_item_number; j<n; j++)
			{
				menu[j].food_name=menu[j+1].food_name;
				menu[j].amount_of_food_quantities=menu[j+1].amount_of_food_quantities;
				menu[j].price=menu[j+1].price;
			}
		}
	}
	n=n-1;
	print();
}

void food_menu()
{
	for(int i=1; i<12; i++)
	{
		int len = food[i].food_name.size();
		cout<<i<<".";
		cout<<food[i].food_name;
		for(int j=0; j<(42-len); j++)
		{
			cout<<"-";
		}
		cout<<">"<<food[i].food_price<<"\n";
	}
	cout<<"12.End the Order\n";
}

void password()
{
	int password;
	cout<<"Enter the password:";
	cin>>password;
	if(password==242002140||password==242002113)
	{
		cout<<"total amount of money= "<<total<<"\n";
	}
	else
	{
		cout<<"you are not a owner in this restaurant.";
	}
}
int main()
{
	ac();
	cout<<"1.Display Food Menu.\n2.Order food.\n3.Chang the food item.\n4.Delete food item.\n5.Print of the all food list and total money .\n6.n=0\n";
	int topice;
	do
	{
		cout<<"Enter topice:";
		cin>>topice;
		if(topice==1)
		{
			food_menu();
			cout<<"\n";
		}
		else if(topice==2)
		{
			food_information();
			cout<<"\n";
		}
		else if(topice==5)
		{
			print();
			cout<<"\n";
		}
		else if(topice==3)
		{
			chang_food_item();
			cout<<"\n";
		}
		else if(topice==4)
		{
			delete_food_item();
			cout<<"\n";
		}
		else if(topice==6)
		{
			n=0;
			total_amount_money=0;
		}
		else if(topice==7)
		{
			cout<<"1.see the total amount of today and  I know password.\n2.No ,I am not a owner in this restaurant.\n ";
			int c;
			cout<<"enter c:";
			cin>>c;
			if(c==1)
			{
				password();
			}
		}
	}
	while(topice<8);
}
