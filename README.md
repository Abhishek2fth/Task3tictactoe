#include <iostream>
#include<string>
using namespace std;
 void  create_playground();
 void  player_enter();
 bool  game_winner ();
char play_grid [3][3]= {{'1','2','3'},{'4','5','6'},{'7','8','9'}};
string ist ="";
string iind="";
int row;
int col;
bool tie = false;
char token ='x';
int main (){
  cout << "enter the name of first player : ";
  getline (cin,ist);
  cout << "enter the name of second player : ";
  getline (cin,iind);
  cout<<endl<<ist<<" is playler one so he /she play first \n"<<iind<<" is second player so he paly second \n" ; 
  while (!game_winner ())
    {
       create_playground();
       player_enter();
       game_winner ();
    }
  if (token =='x'&&tie ==false)
    {
      cout<<"coungrulation! "<<ist<<" you win the match\n";
    }
  else if (token =='o'&&tie ==false)
    {
      cout<<"coungrulation! "<<iind<<" you win the match\n";
    }
  else {
    cout<<"draw,don't worry , play again\n ";
    
  }
  return 0;
}
// creating playground 
void create_playground() {
  cout<<"    |    |    "<<endl;
  cout <<" "<<play_grid[0][0]<<"  |"<<" "<<play_grid[0][1]<<"  |"<<" "<<play_grid[0][2]<<"  "<<endl;
  cout<<"    |    |    "<<endl;
  cout<<"____|____|____"<<endl;
  cout<<"    |    |    "<<endl;
  cout <<" "<<play_grid[1][0]<<"  |"<<" "<<play_grid[1][1]<<"  |"<<" "<<play_grid[1][2]<<"   "<<endl;
  cout<<"    |    |    "<<endl;
  cout<<"____|____|____"<<endl;
  cout<<"    |    |    "<<endl;
  cout <<" "<<play_grid[2][0]<<"  |"<<" "<<play_grid[2][1]<<"  |"<<" "<<play_grid[2][2]<<"  "<<endl;
  cout<<"    |    |    "<<endl;
  
}
 // player enter there logic 
  void player_enter(){
  int digit ;
  if (token=='x')
  {
    cout <<ist<<" enter : ";
    cin>>digit;
  }
  if (token=='o')
  {
    cout <<iind<<" enter : ";
    cin>>digit;
  }
  if (digit ==1)
  {
    row =0;
    col=0;
  }
   else if (digit ==2)
  {
    row =0;
    col=1;
  } 
  else if (digit ==3)
  {
    row =0;
    col=2;
  } 
  else if (digit ==4)
  {
    row =1;
    col=0;
  } 
  else if (digit ==5)
  {
    row =1;
    col=1;
  } 
  else if (digit ==6)
  {
    row =1;
    col=2;
  } 
  else if (digit ==7)
  {
    row =2;
    col=0;
  }
  else if (digit ==8)
  {
    row =2;
    col=1;
  } 
  else if (digit ==9)
  {
    row =2;
    col=2;
  }
  else 
    {
      cout<<"you are enter invalid value,try again\n";
    }
  if (token=='x'&&play_grid[row][col]!='x'&&play_grid[row][col]!='o')
  {
    play_grid[row][col]='x';
    token ='o';
  }
  else  if (token=='o'&&play_grid[row][col]!='x'&&play_grid[row][col]!='o')
  {
    play_grid[row][col]='o';
    token ='x';
  }
  else {
    cout<<"there is no empty space\n";
    //func2();
    return;
  }
}
// decideing game winer 
bool game_winner ()
{
  for (int i = 0;i<3;i++)
    {
      if ((play_grid[i][0]==play_grid[i][1]&&play_grid[i][0]==play_grid[i][2])||(play_grid[0][i]==play_grid[1][i]&&play_grid[0][i]==play_grid[2][i]))
    {
      return true;
    }
    }
  if ((play_grid[0][0]==play_grid[1][1]&&play_grid[0][0]==play_grid[2][2])||(play_grid[0][2]==play_grid[1][1]&&play_grid[0][2]==play_grid[2][0]))
  {
    return true;
  }
  for (int i = 0; i<3; i++)
    {
      for (int j=0;j<3;j++)
    {
      if (play_grid[i][j]!='x'&&play_grid[i][j]!='o')
      {
        return false;
      }
    }
    }
  tie = true;
  return false;
}
