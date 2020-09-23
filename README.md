<div align="center">

## mouse click


</div>

### Description

it is a code that allows the use of mouse in text maode. i found many codes that used mouse in graphical mode but none for text mode. this is my way of solving it. feel free to vote for me
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mohammed Ali Akbani](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mohammed-ali-akbani.md)
**Level**          |Beginner
**User Rating**    |3.3 (13 globes from 4 users)
**Compatibility**  |C\+\+ \(general\), Borland C\+\+
**Category**       |[Documents](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/documents__3-27.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mohammed-ali-akbani-mouse-click__3-1033/archive/master.zip)





### Source Code

```

//	Author:		Mohammed Ali Akbani
//	E-mail:		duke@samwonline.com
//	Level :		beginner
//Please do not repost it in you name and vote for me.
#include<iostream.h>
#include<stdlib.h>
#include<stdio.h>
#include<conio.h>
#include<dos.h>
class mouse
{
 private:
   union REGS i,o;
   struct SREGS s;
 public:
   mouse()
   {
    initmouse();
    showmouseptr();
   }
   void initmouse()
   {
    i.x.ax=0;
    int86(0x33,&i,&o);
   }
   void showmouseptr()
   {
    i.x.ax=1;
    int86(0x33,&i,&o);
   }
   void getmousepos(int& button,int& x,int& y)
   {
    i.x.ax=3;
    int86(0x33,&i,&o);
    button= o.x.bx;
    x=o.x.cx;
    y=o.x.dx;
   }
};
int x=0,y=0,button=0;
mouse m;
int controller=1;
struct btn
{
	int bx1;
	int by1;
	int bx2;
	int by2;
};
void main()
{
// int gdriver = DETECT, gmode;
// initgraph(&gdriver, &gmode, "\\borlandc\\bgi");
	clrscr();
	gotoxy(2,2);
	cout<< "CLICK";
	btn b1 = {0,0,48,16};
	gotoxy(2,4);
	cout<< "CLICK";
	btn b2 ={0,16,48,32};
	gotoxy(2,6);
	cout<< "CLICK";
	btn b3 = {0,32,48,48};
	m.showmouseptr();
	while((!kbhit())&&(controller==1))
	{
		m.getmousepos(button,x,y);
		gotoxy(20,20);
		cout<< x << " " << y;
		if((x>b1.bx1)&&(y>b1.by1)&&(x<b1.bx2)&&(y<b1.by2)&&(button==1))
		{
			delay(300);
			gotoxy(12,12);
			cout << "You clicked #1";
		}
		else if((x>b2.bx1)&&(y>b2.by1)&&(x<b2.bx2)&&(y<b2.by2)&&(button==1))
		{
			delay(300);
			gotoxy(12,12);
			cout << "You clicked #2";
		}
		else if((x>b3.bx1)&&(y>b3.by1)&&(x<b3.bx2)&&(y<b3.by2)&&(button==1))
		{
			delay(300);
			gotoxy(12,12);
			cout<< "You clicked #3";
		}
	}
}
```

