            // Develop a Sales Management System
            // 1. Store the details of the sales people in a company to a text file
            // 2. Retrieve the details of the sales person using ID, phone number, etc..
            // 3. Store the sales details of the sales people to a text file
            // 4. Generate a summary report of the sales.
 
            //  1. Store the details of the sales people in a company to a text file

            // this program is going to create sales people details based on user input
            #include<stdio.h> // include header files
            // beginning of C program
            int main(){
              // declare variables
              char first_name[20];
              char dob[20]; // for date of birth
              char mobile_num[20];
              char nic_num[20]; // for ienty card number
              char date[20]; // for joined date with company
              int user_id;
              float basic_salary;

              FILE *cPtr; // file pointer
    
              cPtr = fopen("sales_people_details.txt", "w"); // open file for writing

              if(cPtr == NULL){
                  printf("Cannot create file\n");
                  return -1;
              }
              // starting to create file
              while(user_id != 0){
                printf("User ID: ");
    	          scanf("%d", &user_id);
                if(user_id != 0){
                    printf("Enter the first name: ");
                    scanf("%s", first_name);
                    printf("Enter NIC number: ");
                    scanf("%s", nic_num);
                    printf("Enter phone number: ");
                    scanf("%s", mobile_num);
                    printf("Date of birth(DD/MM/YYYY): ");
                    scanf("%s", dob);
                    printf("Enter Joined Date(DD/MM/YYYY): ");
                    scanf("%s", date);
                    printf("Basic salary: ");
                    scanf("%f", &basic_salary);
                    printf("\n");
                    fprintf(cPtr,"%d\t%s\t%s\t%s\t%s\t%s\t%.2f\n", user_id, first_name, nic_num, mobile_num, dob, date, basic_salary);

                }
           ` }
               `fclose(cPtr); // close the file
                return 0; //end of C program
          }
          
          
             // 2. Retrieve the details of the sales person using ID, phone number, etc..

            // this program is going to display sales people details based on user input
            #include<stdio.h> // include header files
            // beginning of C program
            int main(){
              // declare variables
              int wanted_id = 1;
              int user_id;
              char first_name[20];
              char nic_num[20];
              char mobile_num[20];
              char dob[20];
              char date[20];
              float basic_salary;

              FILE *fPtr; // file pointer

              fPtr = fopen("sales_people_details.txt", "r"); // open file for reading

              if(fPtr == NULL){
                printf("File not exist");
                return -1;
              }
              while(wanted_id != 0){
                  printf("Enter wanted ID: ");
                  scanf("%d", &wanted_id);
                  fscanf(fPtr, "%d %s %s %s %s %s %f", &user_id, first_name, nic_num, mobile_num, dob, date, &basic_salary);
                  rewind(fPtr);
                  while(!feof(fPtr)){
                    if(user_id == wanted_id){
                      printf("Name: %s\n", first_name);
                      printf("NIC Number: %s\n", nic_num);
                      printf("Mobile Number: %s\n", mobile_num);
                      printf("Date of Birth: %s\n", dob);
                      printf("Joined Date: %s\n", date);
                      printf("Basic Salary: %.2f\n", &basic_salary);
                      break;
                    }
                  fscanf(fPtr, "%d %s %s %s %s %s %f", &user_id, first_name, nic_num, mobile_num, dob, date, &basic_salary);
                  }
                  rewind(fPtr);
              }
              fclose(fPtr); // close the file
              return 0; // end of the C program
            }
            
            
             // 3. Store the sales details of the sales people to a text file
             
            // this program is going to create sales details based on user input
            #include<stdio.h> // include header files
            // beginning of C program
            int main(){
              // declare variables
              double user_id;
              float total_sales_amount;
              int sales_count;

              FILE *cfPtr; // file pointer

              cfPtr = fopen("sales_details", "w"); // open file for writing

              if(cfPtr == NULL){
                    printf("Cannot create file\n");
                    return -1;
                }
                // starting to create file
              while(user_id != 0){
                printf("Enter User ID: ");
                scanf("%d", &user_id);
                if(user_id != 0){
                  printf("Enter Total Sales Amount: ");
                  scanf("%f", &total_sales_amount);
                  printf("Enter Total Sales Count: ");
                  scanf("%d", &sales_count);
                  printf("\n");
                  fprintf(cfPtr, "%d\t%.2f\t%d\n", user_id, total_sales_amount, sales_count);
                }
              }
              fclose(cfPtr); // close the file
              return 0; // end of the C program
            }
            
            
           // 4. Generate a summary report of the sales.
   
          // this program is going to create summary report based on exsiting file
          #include<stdio.h> // include header files
          // beginning of C program
          int main(){
            // declare variables
            int user_id;
            float sales_amount;
            float distance;
            float average_sales_amount = 0.00;
            int sales_count;


            FILE *rPtr; // file pointer
            FILE *sPtr; // file pointer

            rPtr = fopen("sales_details.txt", "r");  // open file for reading
            sPtr = fopen("summary_report.txt", "w"); // open file for writing

            if(rPtr == NULL){
              printf("File no exist\n");
              return -1;
            }
            // starting to create file
            while(!feof(rPtr)){
              fscanf(rPtr, "%d %f %d", &user_id, &sales_amount, &sales_count);
              average_sales_amount = sales_amount / sales_count;
              if(average_sales_amount < 30000.00){
                char status[20] = "Low";
                fprintf(sPtr, "%d\t%f\t%s\n", user_id, average_sales_amount, status);
              }
              if(average_sales_amount >= 30000.00 && average_sales_amount < 40000.00){
                char status[20] = "Average";
                fprintf(sPtr, "%d\t%f\t%s\n", user_id, average_sales_amount, status);
              }
              if(average_sales_amount >= 40000.00 && average_sales_amount < 50000.00){
                char status[20] = "Good";
                fprintf(sPtr, "%d\t%f\t%s\n", user_id, average_sales_amount, status);
              }
              if(average_sales_amount > 50000.00){
                char status[20] = "Excellent";
                fprintf(sPtr, "%d\t%f\t%s\n", user_id, average_sales_amount, status);
              }
              average_sales_amount = 0.00;
            }
            fclose(rPtr); // close the file
            fclose(sPtr); // close the file

            return 0; // end of C program
          }
