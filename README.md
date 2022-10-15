# table
#include<iostream>
#include<string>
#include<cmath>
#include<iomanip>

using namespace std;

int main() {

    // Variable Declaration
    double x1, x2, x3, y1, y2, y3, x_mean, y_mean, m_slope, b_intercept, corr_coefficient;
    int set_precision;
    int x_length;
    string x_label, y_label;

    // User Prompts to gather 3 x and y values, their respective labels, and level of precision
    cout << "Enter your first x- and y-values separated by a space: ";
    cin >> x1 >> y1;
    cout << "Enter your second x- and y-values separated by a space: ";
    cin >> x2 >> y2;
    cout << "Enter your third x- and y-values separated by a space: ";
    cin >> x3 >> y3;
    cout << "Enter your x-label: ";
    cin.ignore();
    getline(cin, x_label);   // Collects entire line of text

    cout << "Enter your y-label: ";
    getline(cin, y_label);    // getline collects entire line of text
    cout << "What level of precision would you like? ";
    cin >> set_precision;     // Number of digits to include or degree of precision


    // Formulas to calcaulate average of x and y
    x_mean = (x1 + x2 + x3) / 3;   // mean of x
    y_mean = (y1 + y2 + y3) / 3;   // mean of y
    // Formula to calculate slope
    m_slope = ((x1 - x_mean) * (y1 - y_mean) + (x2 - x_mean) * (y2 - y_mean) + (x3 - x_mean) * (y3 - y_mean)) / ((x1 - x_mean) * (x1 - x_mean) + (x2 - x_mean) * (x2 - x_mean) + (x3 - x_mean) * (x3 - x_mean));
    // Calculate b intercept
    b_intercept = y_mean - m_slope * x_mean;
    // Correlation Coefficient formula
    corr_coefficient = ((x1 - x_mean) * (y1 - y_mean) + (x2 - x_mean) * (y2 - y_mean) + (x3 - x_mean) * (y3 - y_mean)) / (((x1 - x_mean) * (x1 - x_mean) + (x2 - x_mean) * (x2 - x_mean) + (x3 - x_mean) * (x3 - x_mean)) * ((y1 - y_mean) * (y1 - y_mean) + (y2 - y_mean) * (y2 - y_mean) + (y3 - y_mean) * (y3 - y_mean)));

    // Table Display
    x_length = x_label.length(); // Assigns input/character length of x_label to x_length
    cout << setw(x_length) << x_label << "|" << y_label << '\n';
    cout << setfill('-') << setw(x_length + y_label.length() + 1) << "-" << '\n';
    cout << setfill(' ') << setprecision(set_precision) << fixed;
    cout << setw(x_length) << x1 << "|" << y1 << '\n';
    cout << setw(x_length) << x2 << "|" << y2 << '\n';
    cout << setw(x_length) << x3 << "|" << y3 << '\n';
    cout << "The best fitting equation is: y = " << m_slope << "x + " << b_intercept << '\n';
    cout << "The correlation coefficient is: " << corr_coefficient << '\n';


    return 0;
}
