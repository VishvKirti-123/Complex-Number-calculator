# ifndef COMPLEX_H
# define COMPLEX_H

# include<iostream>
using namespace std;
class Complex
{
protected:
double real;
double imag;
 public:
 Complex();
 Complex(double r, double i);
 void input();
 void display() const;
 Complex add(add Comples &c);
 Complex subtract(const Complex &c);
 Complex multiply(const Complex &c);
 Complex divide(const Complex &c);

double getReal() const;
double getImag() const;
};
#endif

# ifndef OPERATION_H
# define OPERATIONS_H
# include "complex.h"
class Operation 
{
public :
virtual void perform(Complex &c1, Complex &c2) = 0;
virtual ~Operation()
{}
};



