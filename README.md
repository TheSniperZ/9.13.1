# 9.13.1
多文件结构和类的静态成员及静态函数的使用

头文件："Client.h"
#ifndef CLIENT_H_ //编译预处理指令，避免重复包含头文件
#define CLIENT_H_

class Client{
	static char ServerName;
	static int ClientNum;

public:
	static void ChangeServerName(char name);
	static int getClientNum();

};

#endif;

源程序："Client.cpp"
#include "stdafx.h"
#include "client.h"
#include<iostream>
using namespace std;
void Client::ChangeServerName (char name){
	Client::ServerName =name;
	Client::ClientNum ++;  //静态数据成员的访问

}

int Client::getClientNum (){

	return Client::ClientNum ;
}

源程序：// 9.13.1多文件.cpp : 定义控制台应用程序的入口点。
//

#include "stdafx.h"
#include"client.h"
#include<iostream>
 using namespace std;

 int Client::ClientNum =0;
 char Client::ServerName ='a'; //静态数据成员需在类外进行单独初始化

int _tmain(int argc, _TCHAR* argv[])
{
	 Client c1;
	 c1.ChangeServerName('a');
	 cout<<c1.getClientNum() <<endl; //函数后的小括号不能丢
	 Client c2;
	 c2.ChangeServerName('b');
	 cout<<c2.getClientNum() <<endl;
	return 0;
}
