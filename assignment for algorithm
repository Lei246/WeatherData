#include <fstream>
#include <string>
#include <chrono>
#include <iostream>
using namespace std;
typedef std::chrono::high_resolution_clock Clock;

//delare a structure so we can work with different types of data later
struct s
{
	string date;
	double meantempIn;
	double meantempOut;
	int meanhumIn;
	int meanhumOut;
	double moldIndex;

}s_var[300];


//Bubble Sort Functions //it is a fast sorting method for a almost sorted array.
  //swap the positions of two elements
void swap(s* xp, s* yp)
{
	s temp = *xp;
	*xp = *yp;
	*yp = temp;
}


  //swap neighborhood elements if they are in wrong order
  //sort mean temprature_in from hottest to coldest
void bubbleSorttempin(s s_var[], int n)
{
	int i, j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0; j < n - i - 1; j++)
		{
			if (s_var[j].meantempIn < s_var[j + 1].meantempIn)
			{
				swap(&s_var[j], &s_var[j + 1]);
			}
		}
	}
}

  //sort mean temprature_out from hottest to coldest
void bubbleSorttempout(s s_var[], int n)
{
	int i, j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0; j < n - i - 1; j++)
		{
			if (s_var[j].meantempOut < s_var[j + 1].meantempOut)
			{
				swap(&s_var[j], &s_var[j + 1]);
			}
		}
	}
}


 //sort mean humidity_in from driest to humidest
void bubbleSorthumin(s s_var[], int n)
{
	int i, j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0; j < n - i - 1; j++)
		{
			if (s_var[j].meanhumIn > s_var[j + 1].meanhumIn)
			{
				swap(&s_var[j], &s_var[j + 1]);
			}
		}
	}
}

 //sort mean humidity_in from driest to humidest
void bubbleSorthumout(s s_var[], int n)
{
	int i, j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0; j < n - i - 1; j++)
		{
			if (s_var[j].meanhumOut > s_var[j + 1].meanhumOut)
			{
				swap(&s_var[j], &s_var[j + 1]);
			}
		}
	}
}

  //sort moldIndex_out from lowest risk to highest risk
void bubbleSortmold(s s_var[], int n)
{
	int i, j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0; j < n - i - 1; j++)
		{
			if (s_var[j].moldIndex > s_var[j + 1].moldIndex)
			{
				swap(&s_var[j], &s_var[j + 1]);
			}
		}
	}
}

  /* Function to print first 5 meantemperature_in */
void printArraytempin(s s_var[], int size)
{
	int i;
	for (i = 0; i < 5; i++)
		cout << s_var[i].date << ": " << s_var[i].meantempIn << "  ";
	cout << endl;
}

/* Function to print first 5 meantemperature_out */
void printArraytempout(s s_var[], int size)
{
	int i;
	for (i = 0; i < 5; i++)
		cout << s_var[i].date << ": " << s_var[i].meantempOut << " ";
	cout << endl;
}

/* Function to print first 5 mean humidity_in */
void printArrayhumin(s s_var[], int size)
{
	int i;
	for (i = 0; i < 5; i++)
		cout << s_var[i].date << ": " << s_var[i].meanhumIn << " ";
	cout << endl;
}

/* Function to print first 5 mean humidity_out */
void printArrayhumout(s s_var[], int size)
{
	int i;
	for (i = 0; i < 5; i++)
		cout << s_var[i].date << ": " << s_var[i].meanhumOut << " ";
	cout << endl;
}

/* Function to print mean moldIndex_out */
void printArraymold(s s_var[], int size)
{
	int i;
	for (i = 0; i < size; i++)
		cout << s_var[i].date << ": " << s_var[i].moldIndex << " ";
	cout << endl;
}



int main() {

	string date, time, inOut, temperature, humidity;
	int i = 0;

	ifstream text("tempdata4c.txt");
	if (text.is_open())
	{
		string currentDate = "";
		string checkDate = "";
		double tempInSum = 0;
		int humInSum = 0;
		double tempOutSum = 0;
		int humOutSum = 0;
		int count = 0;
		int countIn = 0;
		int countOut = 0;
		 
		//read in data from txt file line by line
		while (!text.eof())
		{
			getline(text, date, ' ');
			getline(text, time, ',');
			getline(text, inOut, ',');
			getline(text, temperature, ',');
			getline(text, humidity);



			
				if (date == checkDate)
				{
					if (inOut == "Inne")
					{
						tempInSum += stod(temperature);
						humInSum += stoi(humidity);
						currentDate = date;
						countIn++;
						count++;
					}
					else
					{
						tempOutSum += stod(temperature);
						humOutSum += stoi(humidity);
						currentDate = date;
						countOut++;
						count++;
					}

				}
				else
				{
					checkDate = date;
					if (countIn != 0)
					{
						cout <<i <<endl<< currentDate <<" In temp"<< "  " << tempInSum / countIn << " In humidity " << humInSum / countIn << endl;
						cout << currentDate <<" Out temp"<< "  " << tempOutSum / countOut << " Out humidity " << humOutSum / countOut << endl<<endl;

						//calculate and store mean values in arrays of the structure s_var
						s_var[i].meantempIn = tempInSum / countIn;
						s_var[i].meantempOut = tempOutSum / countOut;
						s_var[i].meanhumIn = humInSum / countIn;
						s_var[i].meanhumOut = humOutSum / countOut;
						s_var[i].date = currentDate;

						//define moldIndex_out and store in arrays of the structure s_var
						if (s_var[i].meanhumOut > 78)
						{
							if (s_var[i].meantempOut < 0|| s_var[i].meantempOut > 50)
								s_var[i].moldIndex = 0;
							else
								if (s_var[i].meantempOut > 15)
									s_var[i].moldIndex = (s_var[i].meanhumOut - 78) / 0.22;
								else
									s_var[i].moldIndex = (s_var[i].meanhumOut - 78) * (s_var[i].meantempOut / 15) * 0.22;
						}
						else
							s_var[i].moldIndex = 0;

						tempInSum = 0;
						humInSum = 0;
						countIn= 0;
						tempOutSum = 0;
						humOutSum = 0;
						countOut = 0;
						checkDate = date;
						i++;
					}
				}
		}
				
		// Enter a date to search for tempratures
		int n = 131;
		string mydate;
		cout << "Type a date: ";
		cin >> mydate;

		for (int i = 0; i < n; i++)
		{
			if (s_var[i].date == mydate)
			{
				cout << mydate <<" temperature inside: "<< s_var[i].meantempIn <<" temperature outside: "<< s_var[i].meantempOut<<endl<<endl;
				//cout << mydate << " " << s_var[i].meanhumIn << " " << s_var[i].meanhumOut << endl << endl;

			}
		}

		// Autumn dates
		for (int i = 0; i < n; i++)
		{
			if (s_var[i].meantempOut < 10 && s_var[i].meantempOut>0 && s_var[i + 1].meantempOut > 0 && s_var[i + 1].meantempOut < 10 && s_var[i + 2].meantempOut > 0 && s_var[i + 2].meantempOut < 10)

				cout << "Autumn: " << s_var[i].date << " Temperature outside " << s_var[i].meantempOut << endl;

		}

		// Winter dates

		for (int i = 0; i < n; i++)
		{
			if (s_var[i].meantempOut < 0 && s_var[i + 1].meantempOut < 0 && s_var[i + 2].meantempOut < 0 && s_var[i + 3].meantempOut < 0 && s_var[i + 4].meantempOut < 0 && s_var[i + 5].meantempOut < 0 && s_var[i + 6].meantempOut < 0)
			{
				cout << "winter: " << s_var[i].date << " Temperature outside " << s_var[i].meantempOut << endl;
			}
		}

		//Sort temperatures and print
		auto t1 = Clock::now();
		bubbleSorttempin(s_var, n);
		cout << "Mean temperatures inside hottest: " << endl;
		printArraytempin(s_var, n);
		cout << endl<<endl;
		auto t2 = Clock::now();

		//Calculate time to sort (bubble sort)
		std::cout << "Duration: " << chrono::duration_cast<chrono::nanoseconds>(t2 - t1).count() * 0.000001
			<< " milliseconds" << endl;

		bubbleSorttempout(s_var, n);
		cout << "Mean temperatures outside hottest: " << endl;
		printArraytempout(s_var, n);
		cout << endl << endl;

		//Sort humidity and print
		bubbleSorthumin(s_var, n);
		bubbleSorthumout(s_var, n);
		cout << "Mean humidity inside driest: " << endl;
		printArrayhumin(s_var, n);
		cout << endl << endl;

		cout << "Mean humidity outside driest: " << endl;
		printArrayhumout(s_var, n);
		cout << endl << endl;


		//Sort moldIndex and print
		bubbleSortmold(s_var, n);
		cout << "moldIndex: " << endl;
		printArraymold(s_var, n);
		cout << endl << endl;


	}

	string y;
	getline(cin, y);
	return 0;

}
