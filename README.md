#include <iostream>
#include <cmath>
#include <ifstream>
#include <vector>
#include <string>
using namespace std;

template<class T>
class Complex
{T r,i;
public: 
Complex():r(0),i(0){}
Complex(T a,T b):r(a),i(b){}
void input()
{cout<<"Real: ";
cin>>"imag: ";
cin>>i;
}
void show()
const{cout<<r<<(i>=0?" + ":"-")<<(i>=0?i:-i)<<"i";}
T real()const{return r;}
T imag()const{return i;}
void set (T a,T b)
{r=a;
i=b;
}
Complex add(const Complex&c)const{return Complex(r+c,i+c.i);}
Complex sub(const Complex&c)const{return Complex(r-c,i-c.i);}
Complex mul(const Complex&c)const{return Complex(r*c.r-i*c.i,r*c.i+i*c.r);}
Complex div(const Complex&c)const{T d=c.r*c.r+c.i*c.i;
if(d==0)
throw string("Divide by zero");
return Complex((r*c.+i*c.i)/d,(i*c.r-r*c.i)/d);
};




