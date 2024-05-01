//construction-management
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

Typedef struct {
    Char itemname[20];
    Float mrp, total;
    Int gst;
} Item;

Typedef struct {
    Char itemname[20];
    Float tons, perton, total;
    Int gst;
} Material;

Typedef struct {
    Char company[100];
    Char name[100];
    Int plotno;
    Char phno[15];
    Char address[200];
} Details;

Void calculate(Item *items, int n);
Void calculateMaterials(Material *materials, int n);
Float calculateTotalCost(Item *electricalItems, int numElectrical, Item *plumbingItems, int numPlumbing, Material *materials, int numMaterials);
Void displayInvoice(Details d, Item *electricalItems, int numElectrical, Item *plumbingItems, int numPlumbing, Material *materials, int numMaterials, float totalConstructionCost);

Int main() {
    Int numElectrical, numPlumbing, numMaterials;
    Details d;

    Printf(“Enter name of the construction company: “);
    Fgets(d.company, sizeof(d.company), stdin);
    d.company[strcspn(d.company, “\n”)] = 0;

    printf(“Enter name of the customer: “);
    fgets(d.name, sizeof(d.name), stdin);
    d.name[strcspn(d.name, “\n”)] = 0;

    printf(“Enter plot number: “);
    scanf(“%d”, &d.plotno);

    printf(“Enter phone number: “);
    scanf(“%s”, d.phno);

    // Flush stdin buffer to clear any leftover input
    While (getchar() != ‘\n’);

    Printf(“Enter the address: “);
    Fgets(d.address, sizeof(d.address), stdin);
    d.address[strcspn(d.address, “\n”)] = 0;

    printf(“Electrical work\n”);
    printf(“Enter the number of electrical items purchased: “);
    scanf(“%d”, &numElectrical);

    // Allocate memory for electrical items
    Item *electricalItems = (Item *)malloc(numElectrical * sizeof(Item));
    If (electricalItems == NULL) {
        Printf(“Memory allocation failed\n”);
        Return -1;
    }
    Calculate(electricalItems, numElectrical);

    Printf(“Plumbing work\n”);
    Printf(“Enter the number of plumbing items purchased: “);
    Scanf(“%d”, &numPlumbing);

    // Allocate memory for plumbing items
    Item *plumbingItems = (Item *)malloc(numPlumbing * sizeof(Item));
    If (plumbingItems == NULL) {
        Printf(“Memory allocation failed\n”);
        Free(electricalItems);
        Return -1;
    }
    Calculate(plumbingItems, numPlumbing);

    Printf(“Construction materials\n”);
    Printf(“Enter the number of construction materials purchased: “);
    Scanf(“%d”, &numMaterials);

    // Allocate memory for materials
    Material *materials = (Material *)malloc(numMaterials * sizeof(Material));
    If (materials == NULL) {
        Printf(“Memory allocation failed\n”);
        Free(electricalItems);
        Free(plumbingItems);
        Return -1;
    }
    calculateMaterials(materials, numMaterials);

    // Calculate the total cost
    Float totalConstructionCost = calculateTotalCost(electricalItems, numElectrical, plumbingItems, numPlumbing, materials, numMaterials);

    // Display the invoice
    displayInvoice(d, electricalItems, numElectrical, plumbingItems, numPlumbing, materials, numMaterials, totalConstructionCost);

    // Free allocated memory
    Free(electricalItems);
    Free(plumbingItems);
    Free(materials);

    Return 0;
}

Void calculate(Item *items, int n) {
    Int I;
    For (I = 0; I < n; i++) {
        Printf(“Enter item name: “);
        Scanf(“%s”, items[i].itemname);

        Printf(“Enter MRP: “);
        Scanf(“%f”, &items[i].mrp);

        Printf(“Enter GST: “);
        Scanf(“%d”, &items[i].gst);

        // Calculate total cost
        Items[i].total = items[i].mrp + ((items[i].gst / 100.0) * items[i].mrp);
    }
}

Void calculateMaterials(Material *materials, int n) {
    Int I;
    For (I = 0; I < n; i++) {
        Printf(“Enter item name: “);
        Scanf(“%s”, materials[i].itemname);

        Printf(“Enter total tons: “);
        Scanf(“%f”, &materials[i].tons);

        Printf(“Enter cost per ton: “);
        Scanf(“%f”, &materials[i].perton);

        Printf(“Enter GST: “);
        Scanf(“%d”, &materials[i].gst);

        // Calculate total cost
        Materials[i].total = materials[i].tons * materials[i].perton * (1 + materials[i].gst / 100.0);
    }
}

Float calculateTotalCost(Item *electricalItems, int numElectrical, Item *plumbingItems, int numPlumbing, Material *materials, int numMaterials) {
    Float total = 0;
    Int I;

    // Calculate total cost for electrical items
    For (I = 0; I < numElectrical; i++) {
        Total += electricalItems[i].total;
    }

    // Calculate total cost for plumbing items
    For (I = 0; I < numPlumbing; i++) {
        Total += plumbingItems[i].total;
    }

    // Calculate total cost for materials
    For (I = 0; I < numMaterials; i++) {
        Total += materials[i].total;
    }

    Return total;
}

Void displayInvoice(Details d, Item *electricalItems, int numElectrical, Item *plumbingItems, int numPlumbing, Material *materials, int numMaterials, float totalConstructionCost) {
    Printf(“\n\n*** Invoice ***\n”);
    Printf(“Construction Company: %s\n”, d.company);
    Printf(“Customer Name: %s\n”, d.name);
    Printf(“Plot Number: %d\n”, d.plotno);
    Printf(“Phone Number: %s\n”, d.phno);
    Printf(“Address: %s\n”, d.address);

    // Display electrical items
    Printf(“\nElectrical Items:\n”);
    For (int I = 0; I < numElectrical; i++) {
        Printf(“    Item: %-20s MRP: %.2f GST: %d%% Total: %.2f\n”, electricalItems[i].itemname, electricalItems[i].mrp, electricalItems[i].gst, electricalItems[i].total);
    }

    // Display plumbing items
    Printf(“\nPlumbing Items:\n”);
    For (int I = 0; I < numPlumbing; i++) {
        Printf(“    Item: %-20s MRP: %.2f GST: %d%% Total: %.2f\n”, plumbingItems[i].itemname, plumbingItems[i].mrp, plumbingItems[i].gst, plumbingItems[i].total);
    }

    // Display construction materials
    Printf(“\nConstruction Materials:\n”);
    For (int I = 0; I < numMaterials; i++) {
        Printf(“    Item: %-20s Total Tons: %.2f Cost per Ton: %.2f GST: %d%% Total: %.2f\n”, materials[i].itemname, materials[i].tons, materials[i].perton, materials[i].gst, materials[i].total);
    }

    // Display total construction cost
    Printf(“\nTotal cost of construction: %.2f\n”, totalConstructionCost);
}
 
