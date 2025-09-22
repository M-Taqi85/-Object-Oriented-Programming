# Author
Muhammad Taqi
amk1001851@student.hamk.fi

# Object-Oriented Programming – Assignment  

1. **Student Grade Management System**  
2. **Banking System**  

---

## 📝 Problem 1: Student Grade Management System  

### 🔹 Code  
```csharp
using System;

namespace StudentGradeSystem
{
    class Program
    {
        static void Main(string[] args)
        {
            
            int numStudents = 3;

           
            string[] names = { "ALI", "TAQI", "ASIM" };
            int[] marks = { 92, 78, 65 }; 
            char[] grades = new char[numStudents];
            string[] remarksArray = new string[numStudents];

            
            for (int i = 0; i < numStudents; i++)
            {
                grades[i] = CalculateGrade(marks[i]);
                remarksArray[i] = GetRemarks(grades[i]);
            }

            
            Console.WriteLine("\n--- Student Results ---");
            for (int i = 0; i < numStudents; i++)
            {
                
                PrintResult(names[i], marks[i]);

                
                PrintResult(names[i], marks[i], remarksArray[i]);
            }

            
            int highestIndex = FindHighestScorer(marks);
            Console.WriteLine($"\n--- Highest Scorer ---");
            Console.WriteLine($"{names[highestIndex]} scored the highest with {marks[highestIndex]} marks (Grade: {grades[highestIndex]}, Remarks: {remarksArray[highestIndex]})");
        }

       
        static char CalculateGrade(int marks)
        {
            if (marks >= 90) return 'A';
            else if (marks >= 75) return 'B';
            else if (marks >= 50) return 'C';
            else return 'F';
        }

        
        static string GetRemarks(char grade)
        {
            switch (grade)
            {
                case 'A': return "Excellent";
                case 'B': return "Very Good";
                case 'C': return "Needs Improvement";
                case 'F': return "Fail";
                default: return "Unknown";
            }
        }

        
        static int FindHighestScorer(int[] marks)
        {
            int maxIndex = 0;
            for (int i = 1; i < marks.Length; i++)
            {
                if (marks[i] > marks[maxIndex])
                {
                    maxIndex = i;
                }
            }
            return maxIndex;
        }

        
        static void PrintResult(string name, int marks)
        {
            char grade = CalculateGrade(marks);
            Console.WriteLine($"{name}: Marks = {marks}, Grade = {grade}");
        }

        
        static void PrintResult(string name, int marks, string remarks)
        {
            char grade = CalculateGrade(marks);
            Console.WriteLine($"{name}: Marks = {marks}, Grade = {grade}, Remarks = {remarks}");
        }
    }
}
```


## Screenshot: 

"C:\Users\taqi8\OneDrive - Hämeen ammattikorkeakoulu\Documents\GitHub\Object-Oriented-Programming\student grades.png"

## 📝 Problem 2: Banking System

### 🔹 Code  
```csharp
using System;

namespace BankingSystem
{
    class Program
    {
        static double balance = 1000.0; 

        static void Main(string[] args)
        {
            int choice;

            
            do
            {
                Console.WriteLine("\n--- Banking Menu ---");
                Console.WriteLine("1. Deposit");
                Console.WriteLine("2. Withdraw");
                Console.WriteLine("3. Check Balance");
                Console.WriteLine("4. Exit");
                Console.Write("Enter your choice (1-4): ");

                if (int.TryParse(Console.ReadLine(), out choice) && choice >= 1 && choice <= 4)
                {
                    switch (choice)
                    {
                        case 1:
                            Console.Write("Enter deposit amount: ");
                            if (double.TryParse(Console.ReadLine(), out double depositAmount) && depositAmount > 0)
                            {
                                Deposit(depositAmount);
                            }
                            else
                            {
                                Console.WriteLine("Invalid amount. Must be positive.");
                            }
                            break;
                        case 2:
                            Console.Write("Enter withdrawal amount: ");
                            if (double.TryParse(Console.ReadLine(), out double withdrawAmount) && withdrawAmount > 0)
                            {
                                
                                Console.Write("Apply bank fee? (y/n): ");
                                string feeChoice = Console.ReadLine().ToLower();
                                if (feeChoice == "y")
                                {
                                    Withdraw(withdrawAmount, 10.0);  10)
                                }
                                else
                                {
                                    Withdraw(withdrawAmount); 
                                }
                            }
                            else
                            {
                                Console.WriteLine("Invalid amount. Must be positive.");
                            }
                            break;
                        case 3:
                            CheckBalance(); 
                            break;
                        case 4:
                            Console.WriteLine("Exiting... Thank you!"); 
                            break;
                    }
                }
                else
                {
                    Console.WriteLine("Invalid choice. Please enter 1-4.");
                }
            } while (choice != 4); 
        }

        
        static void Deposit(double amount)
        {
            balance += amount; 
            Console.WriteLine($"Deposited {amount:C}. New balance: {balance:C}");
        }

        
        static void Withdraw(double amount)
        {
            if (balance >= amount) 
            {
                balance -= amount;
                Console.WriteLine($"Withdrawn {amount:C}. New balance: {balance:C}");
            }
            else
            {
                Console.WriteLine("Insufficient funds"); 
            }
        }

        
        static void Withdraw(double amount, double fee)
        {
            double total = amount + fee;
            if (balance >= total) 
            {
                balance -= total;
                Console.WriteLine($"Withdrawn {amount:C} + fee {fee:C}. New balance: {balance:C}");
            }
            else
            {
                Console.WriteLine("Insufficient funds"); 
            }
        }

        
        static void CheckBalance()
        {
            Console.WriteLine($"Current balance: {balance:C}");
        }
    }
}
```


## Screenshot:

"C:\Users\taqi8\OneDrive - Hämeen ammattikorkeakoulu\Documents\GitHub\Object-Oriented-Programming\banking.png"
