#include <stdio.h>
#include <stdlib.h>
#include <string.h>
// Define the structure for a day of the week
struct Day {
 char *dayName;
 int date;
 char *activity;
};
// Function to create a new day entry
struct Day create() {
struct Day newDay;
newDay.dayName = (char *)malloc(20 * sizeof(char)); // Assuming day names won't exceed 20 
characters
 newDay.activity = (char *)malloc(100 * sizeof(char)); // Assuming activity descriptions won't exceed 
100 characters
 printf("Enter Day Name: ");
 scanf("%s", newDay.dayName);
 printf("Enter Date: ");
 scanf("%d", &newDay.date);
 printf("Enter Activity: ");
 scanf(" %99[^\n]s", newDay.activity); // Read up to 99 characters for the activity, leaving space for 
null terminator
 return newDay;
}
// Function to read data from the keyboard and populate the calendar
void read(struct Day calendar[], int numDays) {
 for (int i = 0; i < numDays; i++) {
 printf("Enter details for Day %d:\n", i + 1);
 calendar[i] = create();
 }
}
// Function to display the calendar
void display(struct Day calendar[], int numDays) {
 printf("Calendar:\n");
 for (int i = 0; i < numDays; i++) {
 printf("Day %d: %s\n", i + 1, calendar[i].dayName);
 printf("Date: %d\n", calendar[i].date);
 printf("Activity: %s\n", calendar[i].activity);
 printf("\n");
 }
}
int main() {
 int numDays = 7;
 struct Day calendar[7];
 read(calendar, numDays);
 display(calendar, numDays);
 // Free dynamically allocated memory
 for (int i = 0; i < numDays; i++) {
 free(calendar[i].dayName);
 free(calendar[i].activity);
 }
 return 0;
}
