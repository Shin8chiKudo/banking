#include <stdio.h>
#include <stdlib.h>
#include <conio.h>

int main() {
   Display_Welcome();

   // Account Number
   AccountNumberInput:;
   Get_User_Account_Number();
   if (!Is_Acc_Number_Registered())
   {
      printf("\nYour account number does not exists!\n");
      goto AccountNumberInput;
   }

   // PIN number
   PINInput:;
   
   if (TRIES == 3)
   {
      system("cls");
      printf("For security reasons, the system is temporarily locked.\n");
      printf("The bank staff will come to assist you. Thank you.");
      getch();
      exit(EXIT_FAILURE);
   }

   Get_PIN();
   
   if (!Is_Pin_Ok())
   {
      TRIES++;
      printf("\nIncorrect PIN! You only have %d attempt(s) left.", (3 - TRIES));
      goto PINInput;
   }
   system("cls");
   
   printf("You are now logged in as %s.", UserData.Name);
   
            
}

void Get_PIN() {
   printf("\nEnter your %d-digit PIN number: ", MAX_PIN_LENGTH);
   
   int x = 0;
   while (x < MAX_PIN_LENGTH)
   {
      char ch = getch();
      if (ch >= '0' && ch <= '9')
      {
         printf("*");
         PIN[x] = ch;
         x++;
      } 
      
      else if (ch == 8) // Backspace
      {
         if (x > 0)
            x--;
         
         PIN[x] = '\0';
         system("cls");
         printf("\nEnter your %d-digit PIN number: ", MAX_PIN_LENGTH);
         for (int i = 0; i < x; i++)
         {
            printf("*");
         }
      }
      
   }
}

void Get_User_Account_Number() {
   printf("Type your %d-digit account number: ", MAX_ACCOUNT_NUMBER_LENGTH);

   int x = 0;
   while (x < MAX_ACCOUNT_NUMBER_LENGTH)
   {
      char ch = getch();
      if (ch >= '0' && ch <= '9')
      {
         printf("%c", ch);
         Acc_Number[x] = ch;
         x++;
      } 
      
      else if (ch == 8) // Backspace
      {
         if (x > 0)
            x--;
         
         Acc_Number[x] = '\0';
         system("cls");
         printf("Type your %d-digit account number: ", MAX_ACCOUNT_NUMBER_LENGTH);
         printf("%s", Acc_Number);
         
      }
      
   }
}

void Display_Welcome() {
   printf("Welcome to Banco de Universidad de Filipinas Politecnico\n");
   printf("Press any key to continue.");
   getch();
   system("cls");
}
