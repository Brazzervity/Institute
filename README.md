# Institute
FOR STUDYING
#include <iostream>
#include <fstream>

using namespace std;

void error(int n, float l, float step, float k)
{
	if (n < 2 || l > k || step <= 0) 
	{
		cout << "error";
	}
}
int read1()
{
	int n;
	cout << "Input n:";
	cin >> n;
	return n;
}
float read2()
{
	float l;
	cout << "Input start:";
	cin >> l;
	return l;
}
float read3()
{
	float k;
	cout << "Input end:";
	cin >> k;
	return k;
}
float read4()
{
	float step;
	cout << "Input step:";
	cin >> step;
	return step;
}
float calculate(int n, float x)
{
	if (x < 0)
	{
		float mult = 1;
		for (int i = 0; i <= (n - 1); i++)
		{
			mult += (i * i * i + 3);
		}
		mult = x + mult;
		return mult;
	}
	else
	{
		float sum1 = 0, sum2 = 0;
		for (int i = 1; i <= (n - 1); i++)
		{
			for (int j = 0; j <= i; j++)
			{
				sum2 += x / (i + j);
			}
			sum1 += sum2;
		}
		return sum1;
	}
}
int main() 
{
	float l, k, step;
	int n;
	ofstream fout;
	fout.open("answer.txt");
	try {
		int n = read1();
		float l = read2(), k = read3(), step = read4();
		cout << "Do you want to save to a file: Yes - 1, No - 0 : ";
		int f;
		cin >> f;
		error(n, l, step, k);
		float x = l;
		while (x <= k)
		{
			if (f == 1) 
			{
				fout << "x=" << x << " " << "y=" << calculate(n, x) << endl;
			}
			if (f == 0) 
			{
				cout << "x=" << x << " " << "y=" << calculate(n, x) << endl;
			}
			x += step;
		}
	}
	catch (const char* ex)
	{
		cout << ex << endl;
		return -1;
	}
	catch (...) 
	{
		cout << "error";
		return -2;
	}
}
