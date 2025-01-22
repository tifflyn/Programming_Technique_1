# Programming Technique 1 Assignment 2
The coding below is to create the output required by the question assigned by the professor.

## Assignment2(Q1)

    #include <iostream>
    #include <cmath>
    using namespace std;
    
    double temp(int celsius)
    {
    	double fahrenheit;
    	fahrenheit = celsius * 9/5 +32;
    	return fahrenheit;
    }
    
    void getCategory(double fahrenheit)
    {
    	if(fahrenheit<50)
    	 cout<< "Cold";
    	else if(fahrenheit>=50 && fahrenheit <=77)
      	 cout<<"Moderate";
    	else
     	 cout<<"Hot";
     	 cout<<endl;
     	 
    }

    int main()
    {
    	double celsius,fahrenheit;
    	string category;
    	
	do
	{
		cout<<"Enter temperature in Celsius (-999 to stop): ";
		cin>> celsius;
			
		if(celsius==-999)
		{
			cout<<"Program terminated.";
			break;
		}
		fahrenheit = temp(celsius);
		cout<<"Temperature in Fahrenheit: "<<fahrenheit<<"F"<<endl;
		 
	    cout<<"Category: ";
		getCategory(fahrenheit);
		cout<<endl;
	
	}while (celsius!=-999);
	
	return 0;
    }
    

## Q2
    #include <iostream>
    #include <iomanip> 
    #include <string>
    using namespace std;
    
    void displayBooksBorrowedByStudent(string books[][3], int studentID, int numBooks[], int numStudents);
    void calculateBorrowingStats(int numBooks[], int numStudents, int &totalBooks, int &mostBooksStudent);
    
      int main()
      {
      	const int maxstudent = 10;
      	const int maxbook = 3;
	
	int numStudents;
	string  books[maxstudent][maxbook];
	int numBooks[maxstudent]={0};
	
	cout << "Enter the number of students (max 10): ";
    cin >> numStudents;
    
     for (int i = 0; i < numStudents; i++) 
	 {
        cout << "Enter the number of books borrowed by Student " << i + 1 << " (max 3): ";
        cin >> numBooks[i];
        while (numBooks[i] < 0 || numBooks[i] > 3 )
        {
            cout << "Invalid number of books. Please enter a value between 0 and 3: ";
            cin >> numBooks[i];
        }
        
        cin.ignore();
        for (int j = 0; j < numBooks[i]; j++) 
		{
			 cout << "Enter the title of book " << j + 1 << ": ";
             getline(cin, books[i][j]);
        }
      }
      cout<<endl;
      
      cout<<"Borrowing Records:"<<endl;
      cout<<"Student\tBooks"<<endl;
      for(int i=0;i<numStudents;i++)
      {
      	cout<<i + 1<<"\t";
        for (int j = 0; j < numBooks[i]; j++)
		{
            cout << books[i][j];
            if(j<numBooks[i]-1)cout<<",";
        }
        cout<<endl;
      }
      cout<<endl;
    
    int studentID;
    cout<<endl;
    cout<<"Enter a student ID to view their borrowed books: ";
    cin>>studentID;
    displayBooksBorrowedByStudent(books, studentID, numBooks, numStudents);
    
     int totalBooks = 0;
    int mostBooksStudent = 0;
    calculateBorrowingStats(numBooks, numStudents, totalBooks, mostBooksStudent);
    
    }
    
    void displayBooksBorrowedByStudent(string books[][3], int studentID, int numBooks[], int numStudents)
    {
    	cout << "Books borrowed by Student " << studentID << ":" << endl;
        for (int i = 0; i < numBooks[studentID - 1]; i++) 
    	{
            cout << "- " << books[studentID - 1][i] << endl;
        }
    }
    
    void calculateBorrowingStats(int numBooks[],int numStudents,int &totalBooks,int &mostBooksStudent)
    {
    	totalBooks = 0;
    	mostBooksStudent = 0;
    	int maxBooks=0;
    	for(int i = 0;i<numStudents;i++)
    	{
  		totalBooks += numBooks[i];
  		if(numBooks[i]>maxBooks)
  		{
  			maxBooks = numBooks[i];
  			mostBooksStudent = i + 1;
  		}
  	}
  	cout<<endl;
  	cout<<"Total books borrowed by all students: "<<totalBooks<<endl;
  	cout<<"Student who borrowed the most books: Student "<<mostBooksStudent;
    }

**Reflection:**
This assignment let me explore more library functions such as cmath, iomanip and string, to create more complex programs. Whilst researching more on the libraries, 
I discovered that what I've learned now is just the tip of the iceberg. With this realization, it sparked my exploring interest, then, I fell into 
the rabbit hole of researching and learning more about coding. However, right now I know I must first strengthen my basics.
