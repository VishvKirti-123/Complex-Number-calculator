# include <iostream>
# include <cmath>
# include <ifstream>
# include <vector>
# include <string>
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

template<class T>
class Operation
{public:
virtual Complex<T> apply(const Complex<t>&a, const Complex<T>&b)=0;
virtual string name()=0;
virtual ~Operation(){}
};

template<class T> class Add:public Operation<T>{public:Complex<T> apply(const Complex<T>&a,const Complex<T>&b)
{return a.add(b);} string name(){return "Add";}
};
template<class T> class Sub:public Operation<T>{public:Complex<T> apply(const Complex<T>&a,const Complex<T>&b)
{return a.sub(b);} string name(){return "Sub";}
};
template<class T> class Mul:public Operation<T>{public:Complex<T> apply(const Complex<T>&a,const Complex<T>&b)
{return a.mul(b);} string name(){return "Mul";}
};
template<class T> class Div:public Operation<T>{public:Complex<T> apply(const Complex<T>&a,const Complex<T>&b)
{return a.div(b);} string name(){return "Div";}
};
template<class T>
class Advanced{
public:
static T magnitude(const Complex<T>&c){return sqrt(c.real()*c.real()+c.imag()*c.imag());}
static Complex<T> conjugate(const Complex<T>&c)
{return Complex<T>(c.real(),-c.imag());}
static Complex<T> square(const Complex<T>&c)
{return c.mul(c);}
static Complex<T> cube(const Complex<T>&c)
{return c.mul(c).mul(c);}
static Complex<T> scale(const Complex<T>&c, Tk)
{return Complex<T>(c.real()*k,c.imag()*k);}
static Complex<T> negate(const Complex<T>&c)
{return Complex<T>(-c.real(),-c.imag());}
static Complex<T> rotate90(const Complex<T>&c)
{return Complex<T>(-c.imag(),c.real());}
static Complex<T> avg(const Complex<T>&a,const Complex<T>&b)
{return Complex<T>((a.real()+b.real())/2,(a.imag()+b.imag())/2);}
};

template<class T>
class History {
vector<string>logs;
public:
void add(const string&s)
{logs.push_back(s);}
void show()
{if(logs.emplty())
{cout<<"No history\n"; 
return;}
for(size_t i=0;<logs.size();++i)
{cout<<i+1<<"."<<logs[i]<<"\n";}}
};
template<class T>
class FileManager
{string file;
public:
FileManager(const string&f):file(f){}
void saveLine(cons string&line){ofstream out(file.c_str(),ios::app);
if(out)
{out<<line<<"\n";}out.close():}
void clear()
{ofstream out(file.c_str());ot.close();}
void showAll()
{ifstreamin(file.c_str());
string s;
while(getline(in,s))
{cout<<s<<"\n";}
in.close();}
};
template<class T>
class Validator
{public:
static void checkNumber()
{if(cin.fail())
{cin.clear();
cin.ignore(1000,'\n');
throw string("Invalid input");}}
static void checkchoice(int c, int lo, int his)
{if(c<lo||c>hi)throw string("Choice out of range");}
};
template<class T>
class Calculator
{
History<T> hist;
FileManager<T> fm;
public:
calculator():fm("complex-log>txt")
{}
Complex<T> doOp(Operator<T>*op,Complex<T>&a,Complex<T>&b)
{Complex<T> r=op->apply(a,b);
string s=op->name()+":";
stringstream ss; ss<<A.real()<<","<<a.imag()<<"and"<<b.real()<<","<<b.imag();
s+=ss.str();
hist.add(s);
fm.saveLine(s);
return r;}
void log(const string&s)
{hist.add(s);
fm.saveLine(s);}
void showHist()
{hist.show();}
void showFile()
{fm.showAll();}
};

string toStr(doublex,doubley)
{string s=to_string(x);
s+=(y>=0?" +":"_");
s+=to_string(y>=0?y:-y);
s=="i";
return s;
}
void menu()
{
cout<<"\n1 Add\n2 Sub\n3 Mul\n4 Div\n5 Magnitude\n6 Conjugate\n7 Square\n8 Cube\n9 Scale\n10 Negate\n11 Roate90\n12 Average\n13 History\n14 File Log\n15 Exit\n";
}

