#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>
#include <stdio.h>
#include "student.h"
#include "bubble.h"
using namespace std;

struct classStats{
    float mean;
    float min;
    float max;
    float median;
    char *name;
};

void bubble(student *array[], int size){
    int x;
    int y;
    student *temp = NULL;
    for(x = 0; x < size; x++){
        for(y = 0; y < size - 1; y++){
            if(array[y]->mean > array[y+1]->mean){
                temp = array[y+1];
                array[y+1] = array[y];
                array[y] = temp;
            }
        }
    }
    return;
}

int main(){
    struct classStats stats;
    FILE *myFile;
    string myString;
    string line;
    student *arr[19];
    float sum = 0;
    int size = 19;

    myFile = fopen("grades.txt", "r");
    stats.name = (char *)malloc(20 * sizeof(char));
    fscanf(myFile, "%s", stats.name);

    for(int i =0; i < 19; i++){
        arr[i] = (student *)malloc(20 * sizeof(student));
        arr[i]->first = (char *)malloc(20 * sizeof(char));
        arr[i]->last = (char *)malloc(20 * sizeof(char));
        fscanf(myFile, "%s%s%d%d%d", arr[i]->first, arr[i]->last, &arr[i]->exam1,
        &arr[i]->exam2, &arr[i]->exam3);
        arr[i]->mean = (arr[i]->exam1 + arr[i]->exam2 + arr[i]->exam3) / 3.0; //
        compute average
        sum = sum + arr[i]->mean;
    }

    fclose(myFile);
    bubble(arr, 19);

    stats.max = arr[18]->mean;
    stats.min = arr[0]->mean;
    stats.mean = sum/19;
    stats.median = arr[19/2]->mean;
    printf("%sMEAN: %.2f MIN: %.2f MAX: %.2f MEDIAN: %.2f\n", stats.name, stats.mean, stats.min, stats.max, stats.median);
    
    for(int i =0; i < 19; i++){
        cout << setw(10) << left << setprecision(2) << fixed << arr[i]->first << "\t" << setw(10)<< arr[i]->last << "\t" << arr[i]->mean << endl;
    }

    for (int i = 0; i < 19; i++){
        free(arr[i]->first);
        free(arr[i]->last);
        free(arr[i]);
    }
    return 0;
}
