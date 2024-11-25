#include <stdio.h>

#define MAX 100


int main() {
    char str[MAX], pat[MAX], rep[MAX],result[MAX];
    int i = 0, j = 0, k, found = 0;
    

    printf("Enter the main string (STR): ");
    gets(str);  // Use gets() for simplicity

    printf("Enter the pattern string (PAT): ");
    gets(pat);

    printf("Enter the replace string (REP): ");
    gets(rep);
    
    while (str[i] != '\0') {
        k = 0;
        
        while (pat[k] != '\0' && str[i + k] == pat[k]) {
            k++;
        }

        if (pat[k] == '\0') {
            found = 1;
            for (k = 0; rep[k] != '\0'; k++) {
                result[j++] = rep[k];
            }
            i += k;
        } else {
            result[j++] = str[i++];
        }
    }

    result[j] = '\0';  

    if (found) {
        printf("After replacement: %s\n", result);
    } else {
        printf("Pattern not found.\n");
    }
    return 0;
}
