# WSQ-8_LychrelNumber
This program asks the user for a lower and higher bound value tells them which numbers are Lychrel, natural palyndrome and the non-lychrel that become palyndromes. 
#include <iostream>
using namespace std;

//To make the reversed number
long long swap(long long val) {
  long long changed=0;

  while(val>0) {
    changed=(changed*10)+(val%10);
    val=val/10;
  }
return changed;
}

int LychrelConver(long long val) {
  long long add;
  int resp, tries=0;

  if(val==swap(val)) {
    resp=1;
  } else {
    add=val+swap(val);

      while(tries!=30 && add!=swap(add)) {
        add=add+swap(add);
        tries+=1;
      }

      if(tries==30) {
        resp=2;
        cout << "Lychrel candidate is " << val << endl;
      } else {
          resp=3;
      }
    }
return resp; // The output of this function is either 1, 2, or 3. 
}

int main() {
  int high, low, lychrel=0, first=0, moreTries=0, resp;
  long long val;
  cout << "Give the lower bound of the range of numbers:" << endl;
  cin >> low;
  cout << "Give the upper bound of the range of numbers:" << endl;
  cin >> high;

  val = low;

  for(int i=0; val!=high; i++) {
    val = low + i;
    if(LychrelConver(val)==1){
      first += 1;
    } else if(LychrelConver(val)==2) {
      lychrel += 1;
    } else {
      moreTries += 1;
    }
  }

  cout <<"\x1b[31;1m" << "Lychrel's " << lychrel << endl;
  cout << "Natural palindrome " << first << endl;
  cout << "More tries palindromes " << moreTries << "\x1b[0m\n" << endl;

return 0;
}
