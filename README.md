#include<stdio.h>
#include<conio.h>
int main()
{
    FILE *fp;
    FILE *fp2;
    char ch, fname[30], newch[500];
    int i=0, j, count=0;
    printf("Enter the filename with extension: ");
    gets(fname);
    fp = fopen(fname, "r");
    if(!fp)
    {
        printf("File does not exist!\n Press Enter to continue");
        getch();
        return 0;
    }
    printf("\nThe original content is:\n\n");
    ch = getc(fp);
    while(ch != EOF)
    {
        count++;
        putchar(ch);
        newch[i] = ch;
        i++;
        ch = getc(fp);
    }
    printf("\n\n\n");
    printf("The content in reverse order is:\n\n");
    for(j=(count-1); j>=0; j--)
    {
        ch = newch[j];
        printf("%c", ch);
    }
    printf("\n");
    printf("press any key");
    getch();

printf("\nEnter another filename with extension: ");
gets(fname);
fp2 = fopen(fname, "r");
ch = fgetc(fp);
   while (ch != EOF)
   {
      fputc(ch, fp2);
      ch = fgetc(fp2);
   }
   printf("\nContents copied to %s", fname);
   fclose(fp);
   fclose(fp2);
   return 0;
}
