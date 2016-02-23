//source
// Help taken from github
#include <sstream>
#include <string>
#include <fstream>
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>
#include <time.h>
#include <stdlib.h>
#include "matrixheader.h"


int main(int argc, char* argv[]) {
	string filename;
	if (argc < 3) {
		filename = "2000.in";
	}
	else {
		filename = argv[2];
	}

	if (argc < 5) {
		leafsize = 16;
	}
	else {
		leafsize = atoi(argv[4]);
	}

	srand(time(NULL));
	int n = 2;
	int rows = n;
	int column = n;

	vector<vector<int>> A;
	vector<int> tempSecond;
	for (int i = 0; i<rows; i++){
		for (int j = 0; j<column; j++){
			tempSecond.push_back(rand() % 10);

		}
		A.push_back(tempSecond);
		tempSecond.erase(tempSecond.begin(), tempSecond.end());
	}

	vector<vector<int>> B;
	vector<int> tempFirst;
	for (int i = 0; i<rows; i++){
		for (int j = 0; j<column; j++){
			tempFirst.push_back(rand() % 10);

		}

		B.push_back(tempFirst);
		tempFirst.erase(tempFirst.begin(), tempFirst.end());

	}


	vector<vector<int>> C;
	vector<int> tempThird;
	for (int i = 0; i<rows; i++){
		for (int j = 0; j<column; j++){
			tempThird.push_back(0);
		}

		C.push_back(tempThird);
		tempThird.erase(tempThird.begin(), tempThird.end());

	}


	cout<<"Multiplication using iterative Method....."<<endl;
	vector<vector<int>> R = Multiply(A,B,rows,column);
	printMatrix(R,n);


	cout<<"Multiplication using Strassen's algorithm....."<<endl;
	strassen(A, B, C, n);
	printMatrix(C, n);

	
	
	system("pause");

}
