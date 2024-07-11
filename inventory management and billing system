//  Created by Faaize Shams on 22/08/23.
//
//  include <solo.h>

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Product {
    char p_name[20];
    int p_id;
    int exp;
    float price;
    char p_manu[20];
    char rack[30];
    int dp, mp, yp;
    int de, me, ye;
};

int main() {
    struct Product management[30];
    FILE *fp;
    int choice, i, j, k, m, name, l, z = 0, h, sumf = 0, sum = 0, x = 0, t = 0, g = 0;

    printf("Enter 0 to enter new product details, 1 to update product, or 2 to do billing: ");
    scanf("%d", &choice);

    if (choice == 0) {
        printf("Enter the number of products you want to enter: ");
        scanf("%d", &choice);

        for (i = 0; i < choice; i++) {
            printf("Enter the name of product %d: ", i);
            getchar(); // to clear the newline character left in buffer
            fgets(management[i].p_name, sizeof(management[i].p_name), stdin);

            printf("Enter the product id of product %d: ", i);
            scanf("%d", &management[i].p_id);

            printf("Enter 0 if the product %d can expire in 5 days, otherwise enter 1: ", i);
            scanf("%d", &management[i].exp);

            printf("Enter the price of product %d: ", i);
            scanf("%f", &management[i].price);

            printf("Enter the manufacturer of product %d: ", i);
            getchar(); // to clear the newline character left in buffer
            fgets(management[i].p_manu, sizeof(management[i].p_manu), stdin);

            printf("Enter the place of putting the product %d: ", i);
            fgets(management[i].rack, sizeof(management[i].rack), stdin);

            printf("Enter the date of putting the product %d in the store (dd mm yyyy): ", i);
            scanf("%d %d %d", &management[i].dp, &management[i].mp, &management[i].yp);

            printf("Enter the date of expiry of the product %d (dd mm yyyy): ", i);
            scanf("%d %d %d", &management[i].de, &management[i].me, &management[i].ye);
        }
    } 
    else if (choice == 1) {
        printf("Enter the product id to update: ");
        scanf("%d", &name);

        for (i = 0; i < choice; i++) {
            if (name == management[i].p_id) {
                printf("Enter the name of the product %d: ", i);
                getchar(); // to clear the newline character left in buffer
                fgets(management[i].p_name, sizeof(management[i].p_name), stdin);

                printf("Enter the product id of product %d: ", i);
                scanf("%d", &management[i].p_id);

                printf("Enter the price of product %d: ", i);
                scanf("%f", &management[i].price);

                printf("Enter the manufacturer of product %d: ", i);
                getchar(); // to clear the newline character left in buffer
                fgets(management[i].p_manu, sizeof(management[i].p_manu), stdin);

                printf("Enter the place of putting the product %d: ", i);
                fgets(management[i].rack, sizeof(management[i].rack), stdin);

                printf("Enter the date of putting the product %d in the store (dd mm yyyy): ", i);
                scanf("%d %d %d", &management[i].dp, &management[i].mp, &management[i].yp);

                printf("Enter the date of expiry of the product %d (dd mm yyyy): ", i);
                scanf("%d %d %d", &management[i].de, &management[i].me, &management[i].ye);
            }
        }
    } 
    else if (choice == 2) {
        printf("Enter the number of products for billing: ");
        scanf("%d", &choice);

        printf("Enter the current date (dd): ");
        scanf("%d", &m);

        for (i = 0; i < choice; i++) {
            printf("Enter the product id of product %d: ", i);
            scanf("%d", &name);

            printf("Enter 0 if the product is food product and 1 if it is not: ");
            scanf("%d", &l);

            for (j = 0; j < choice; j++) {
                if (name == management[j].p_id) {
                    if (management[j].exp == 0) {
                        fp = fopen("bill.txt", "w");
                        fprintf(fp, "%d\n", i);
                        fputs(management[j].p_name, fp);
                        fprintf(fp, "%f\n", management[j].price);
                        fclose(fp);

                        k = m - management[j].dp;
                        z = management[j].price;
                        if (k < 0) {
                            k *= -1;
                        }
                        for (h = 1; h <= k; h++) {
                            z = z - ((z * 5) / 100);
                        }
                        if (sum == 0) {
                            sumf = sumf + z;
                        } else {
                            sum = sum + z;
                        }
                    } else {
                        if (sum == 0) {
                            sumf = sumf + management[j].price;
                        } else {
                            sum = sum + management[j].price;
                        }
                    }
                }
            }
        }
    }

    printf("Enter 0 if the user has a membership card and the product is more than Rs. 250, otherwise enter 1: ");
    scanf("%d", &h);

    if (h == 0) {
        if (sum + sumf >= 500) {
            x = sumf + sum;
            t = x - (x * 5 / 100);
            g = t;
            printf("The total cost of the products is %d\n", g);
        }
        if (sumf + sum >= 250 && sumf + sum <= 500) {
            x = sum - (sum * 2 / 100);
            t = sumf - (sumf * 2 / 100);
            if (sumf >= 250) {
                t = sumf - (sumf * 4 / 100);
            }
            g = x + t;
            printf("The total cost of the products is %d\n", g);
        } else {
            g = sumf + sum;
        }
    } else {
        printf("Enter the discount percentage for occasional events (5-10%%): ");
        scanf("%d", &h);
        x = sumf + sum;
        g = g - (g * h / 100);
        printf("The total cost of the products is %d\n", g);
    }

    int bo = sumf + sum;
    fp = fopen("bill.txt", "a");
    fprintf(fp, "Total sum of products is: %d\n", bo);
    fprintf(fp, "Total sum of products after discount is: %d\n", g);
    fclose(fp);

    return 0;
}


