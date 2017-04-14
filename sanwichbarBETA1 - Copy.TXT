#include <stdio.h>
#include <stdlib.h>
#include<ctype.h>

int main()
{
    int pricelist[3][3]={{200,300,100},{250,350,150},{225,325,125}};
    char breadtype,filling,reqsize;
    char *xname;
    char *yname;
    char *toppingname;
    char *sandsize;
    int pricebread,x,y,toppingprice,topping,a,condition1,flag,qty;
    //float qty;
    printf("\t ----------SANDWICH BAR----------\n\n\n");

    //pricelist
    printf("\t**PRICELIST**\n\n");
    printf("Types of bread \t chicken \t sea food \t vegetarian\n");
    printf("Baguette \t %d \t\t %d \t\t %d\n",pricelist[0][0],pricelist[0][1],pricelist[0][2]);
    printf("Foccacia \t %d \t\t %d \t\t %d\n",pricelist[1][0],pricelist[1][1],pricelist[1][2]);
    printf("Ciabatta \t %d \t\t %d \t\t %d\n",pricelist[2][0],pricelist[2][1],pricelist[2][2]);

    printf("\n*Following toppings are available*\n");
    printf("-Cheese: Rs.50\n");
    printf("-Mayomnaise: Rs.25\n");
    printf("-Special sauce: Rs.100\n");

    //getting user input of bread type & storing the input in breadtype variable
    do{
        printf("\nWhat is the type of bread required(B,F,C)?\n ");
        printf("Enter 'E' to exit\n");
        printf("choice: ");
        scanf("%c",&breadtype);
        breadtype=toupper(breadtype);
        if(breadtype=='E'){
            printf("Thank you for using our services.\n");
            return 0;
        }
        switch(breadtype)
        {
            case 'B':{x=0;xname="Baguette";}break;
            case 'F':{x=1;xname="Foccacia";}break;
            case 'C':{x=2;xname="Ciabatta";}break;

        }

    }while(breadtype!='B'&&breadtype!='F'&&breadtype!='C');

    //getting filling requirements from user
    do{
        printf("\nWhat is the filling you require(C,S,V)?\n ");
        printf("Enter 'E' to exit\n");
        printf("choice: ");
        scanf("%c",&filling);
        scanf("%c",&filling);
        filling=toupper(filling);
        if(filling=='E'){
            printf("Thank you for using our services.\n");
            return 0;
        }
        switch(filling)
        {
            case 'C':{y=0;yname="chicken";}break;
            case 'S':{y=1;yname="sea_food";}break;
            case 'V':{y=2;yname="vegetarian";}break;
        }

    }while(filling!='C'&&filling!='S'&&filling!='V');

    //price
    pricebread=pricelist[x][y];

    //size
    do{
        printf("\nWhat is the size you require(S,M,L)?\n ");
        printf("Enter 'E' to exit\n");
        printf("choice: ");
        scanf("%c",&reqsize);
        scanf("%c",&reqsize);
        reqsize=toupper(reqsize);
        if(reqsize=='E'){
            printf("Thank you for using our services.\n");
            return 0;
        }
        switch(reqsize)
        {
            case 'S':{sandsize="small";}break;
            case 'M':{pricebread+=pricebread*0.1;sandsize="medium";}break;
            case 'L':{pricebread+=pricebread*0.2;sandsize="large";}break;
        }

    }while(reqsize!='S'&&reqsize!='M'&&reqsize!='L');


    //topping
    do{
        printf("What is the topping require? ");
        printf("1.Cheese only\n");
        printf("2.Mayomnaise only\n");
        printf("3.Special sauce only\n");
        printf("4.Cheese and Mayomnaise \n");
        printf("5.Cheese and Special sauce\n");
        printf("6.Mayomnaise and Special sauce\n");
        printf("7.Cheese , Mayomnaise and Special sauce\n");
        printf("8. exit\n");
        printf("Choose: ");
        scanf("%d",&topping);
        if(topping=='8'){
            printf("Thank you for using our services.\n");
            return 0;
        }
        switch(topping)
        {
            case 1:{toppingprice=50;toppingname="Cheese";}break;
            case 2:{toppingprice=25;toppingname="Mayomnaise";}break;
            case 3:{toppingprice=100;toppingname="Special sauce";}break;
            case 4:{toppingprice=75;toppingname="Cheese and Mayomnaise";}break;
            case 5:{toppingprice=150;toppingname="Cheese and Special sauce";}break;
            case 6:{toppingprice=125;toppingname="Mayomnaise and Special sauce";}break;
            case 7:{toppingprice=175;toppingname="Cheese , Mayomnaise and Special sauce";}break;
        }
    }while(topping!=1&&topping!=2&&topping!=3&&topping!=4&&topping!=5&&topping!=6&&topping!=7&&topping!=8);

    //price update
    pricebread+=toppingprice;

    //how many
    do
    {

        printf("\nHow many sandwiches of the specified type do you require?\n");
        fflush(stdin);
        scanf(" %d",&qty);
    }while(qty<1||qty>100);


    //priceupdate
    pricebread*=qty;

    //invoice
    /*
    printf("\n\n\n\n-----------------------------------------INVOICE----------------------------------------- \n\n");
    printf("                -ITEM-                                          -QUANTITY-                            -PRICE-\n");
    printf("%s %s  %s %s                  %d                                Rs.%d\n\n\n\n",xname,yname,sandsize,toppingname,qty,pricebread);
*/
    printf("\n\n-----------INVOICE-------------\n\n");
    printf("ITEM NAME :      %s %s %s %s\n",xname,yname,sandsize,toppingname);
    printf("QUANTITY :      %d\n",qty);
    printf("TOTAL PRICE :      Rs.%d\n\n",pricebread);

   return 0;
}
