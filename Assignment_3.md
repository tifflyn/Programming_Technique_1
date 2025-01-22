# Programming Technique 1 Assignment 3
The coding below will produce the output from the question assigned by the professor.

    #include <iostream>
    #include <fstream>
    #include <string>
    #include <iomanip>
    using namespace std;
    
    const int MAX = 20; // Maximum number of universities to store
    // Function prototype
    void getInput(const string input, string universities[], int intake[], int enrolment[], int output[], int& count);
    int calTotal(const int arr[], int Count);
    int getLowest(const int arr[], int Count);
    int getHighest(const int arr[], int Count);



    int main() 
    {
	
    string universities[MAX];
    int intake[MAX];
    int enrolment[MAX];
    int output[MAX];
    int count = 0;
    ifstream inputFile("input.txt");
    ofstream outputFile;
    

    getInput("input.txt", universities, intake, enrolment, output, count);
    
    // 	Calculate and display totals
        int totalIntake = calTotal(intake, count);
        int totalEnrolment = calTotal(enrolment, count);
        int totalOutput = calTotal(output, count);
    
    int lowestIntake = getLowest(intake, count);
    int lowestEnrolment = getLowest (enrolment, count);
    int lowestOutput = getLowest(output, count);
    
    
    int highestIntake = getHighest(intake, count);
    int highestEnrolment = getHighest(enrolment, count);
    int highestOutput = getHighest(output, count);
    
    int rangeIntake = intake[highestIntake] - intake[lowestIntake];
    int rangeEnrolment = enrolment[highestEnrolment] - enrolment[lowestEnrolment];
    int rangeOutput = output[highestOutput] - output[lowestOutput];
    
    double avrgIntake = static_cast<double>(totalIntake)/MAX;
    double avrgEnrolment = static_cast<double>(totalEnrolment)/MAX;
    double avrgOutput = static_cast<double>(totalOutput)/MAX;
    
    //open outputfile
    outputFile.open("output.txt");
    
    //writing into the file
     outputFile<<"\t NUMBER OF STUDENTS' INTAKE, ENROLMENT AND OUTPUT \n\t IN PUBLIC UNIVERSITIES (2024)\n"//can't use endl
      <<"-----------------------------------------------------------------\n\n"
      <<"University"<<setw(15)<<"Intake"<<setw(12)<<"Enrolment"<<setw(10)<<"Output\n\n"
       <<"----------------------------------------------------------------\n\n";

    for (int i = 0; i < count; ++i) 
	{
    	outputFile<< left << setw(6 + 14) << universities[i] 
				  <<setw(10)<<intake[i]
				  <<setw(10)<< enrolment[i] 
				  <<setw(10)<< output[i] 
				  <<endl;
    }
  
    outputFile<<"---------------------------------------------------------\n\n"
    <<left<<setw(18)<<"TOTAL"<<setw(12)<<totalIntake<<setw(10)<<totalEnrolment<<setw(10)<<totalOutput<<endl;
    outputFile<< fixed << setprecision(2);
    outputFile<<left<<setw(18)<<"AVERAGE"<<setw(12)<<avrgIntake<<setw(10)<<avrgEnrolment<<setw(10)<<avrgOutput
    <<"\n\n--------------------------------------------------------\n\n"
    <<"THE LOWEST NUMBER OF STUDENTS' INTAKE = "<<intake[lowestIntake]<<" ("<<universities[lowestIntake]<<")\n"
    <<"THE HIGHEST NUMBER OF STUDENTS' INTAKE = "<<intake[highestIntake]<<" ("<<universities[highestIntake]<<")\n\n"
	
	<<"THE LOWEST NUMBER OF STUDENTS' ENROLMENT = "<<enrolment[lowestEnrolment]<<" ("<<universities[lowestEnrolment]<<")\n"
    <<"THE HIGHEST NUMBER OF STUDENTS' ENROLMENT = "<<enrolment[highestEnrolment]<<" ("<<universities[highestEnrolment]<<")\n\n"
    
    <<"THE LOWEST NUMBER OF STUDENTS' OUTPUT = "<<output[lowestOutput]<<" ("<<universities[lowestOutput]<<")\n"
    <<"THE HIGHEST NUMBER OF STUDENTS' OUTPUT = "<<output[highestOutput]<<" ("<<universities[highestOutput]<<")\n\n"
    
    <<"Range of Intake: "<<rangeIntake
    <<"\nRange of Enrolment: "<<rangeEnrolment
    <<"\nRange of Output: "<<rangeOutput;
    
    //close this file
    	outputFile.close();
    
    
	return 0;
    }
    
    void getInput(const string input, string universities[], int intake[], int enrolment[], int output[], int& count) 
    {
        ifstream inputFile("input.txt");

        if (!inputFile.is_open()) 
        {
            cout << "Error: Could not open the file ./n" ;
            return;
        }

      count = 0; 
      while (!inputFile.eof() && count < MAX) 
  	{
        getline(inputFile, universities[count], ' '); 

        inputFile >> intake[count];       
        inputFile.ignore();               
        inputFile >> enrolment[count];    
        inputFile.ignore();               
        inputFile >> output[count];       
        inputFile.ignore();               

        ++count; 
    }

    inputFile.close();
    }

    int calTotal(const int arr[], int Count) {
        int total = 0;
        for (int i = 0; i < Count; i++) {
            total += arr[i];
        }
        return total;
    }
    
    int getLowest(const int arr[], int Count)
    {
    	int lowestarr=0;
    	for(int i=1; i<Count; i++)
    	{
    		if(arr[i]<arr[lowestarr])
    			lowestarr=i;
    	}
    	return lowestarr;
    }


    int getHighest(const int arr[], int Count)
    {
    	int highestarr=0;
    	for(int i=1; i<Count; i++)
    	{
    		if(arr[i]>arr[highestarr])
    			highestarr=i;
    	}
    	return highestarr;
    }

**Reflection:**
This assignment allowed me to strengthen my basic input-output for C++ programming, with the confusing open file, writing or reading into the file, 
and then closing the file, I managed to understand and apply it in the assignment with my team member.
