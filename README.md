# Python_Notes

MULTI-THREADING:

process- a program dispatched to ready state and CPU for execution
heavy weight
more time 
thread - segment of process
light weight
less time
task -- execution process
multi-tasking: simultaneously runuing multiple tasks
2 types:
process based
thread based

THREAD- light weight process

THREADING- built-in module used for dev threads

multithreading-- 

******** in python program default one thread is created or contain i.e" mainthread"


TO PRINT CURRENT EXECUTING THREAD NAME
import threading
print("current execting thread is " , threading.current_thread().getName())


ways to create thread:
a. creating thread without using any class

from threading import *
def display():
for i in range(1,11):
print("child thread")
t= Thread(target=display)  # creating thread obj
t.start() # starting of thread
for i in rane(1,11):
print("main thread")

b. creating thread by extending thread class

from threading import *
class MyThread(Thread):
def run(self):
for i in range(1,11):
print("child thread")
t=MyThread()
t.start()
for i in range(1,11):
print("main thread")


c. creating thread eithout extending thread class

from threading import *
class Test():
    def run(self):
        for i in range(1,11):
            print("child thread")
obj=Test()
t=Thread(target=obj.run)
t.start()
for i in range(1,11):
    print("main thread")


from threading import *
class Test():
    def display(self):
        for i in range(1,11):
            print("child thread")
obj=Test()
t=Thread(target=obj.display)
t.start()
for i in range(1,11):
    print("main thread")



SET AND GET NAME OF THREADS

setName(new name)---- set our own name
getNmae()--- returns name of thread

from threading import *
print("current execting thread is " , current_thread().getName())
current_thread().setName("sravani")
print("after setting name the current execting thread is " ,current_thread().getName())
print(current_thread().name)

THREAD IDENTIFICATION NO(ident)

from threading import *
    def display(self):
            print("child thread")
t=Thread(target=display)
t.start()
print("main thread",current_thread().ident)
print("child thread",t.ident)


methods:

active_count()--- returns the no of active threads currently running
enumerate()--- returns list of all active threads currently running
isAlive()-- checks whether thread is exec ot not
join()--- thread wants to wait until completing other thread 


DAEMON THREAD:
thread which are running in background 

isDaemon()
setDaemon()

from threading import *
def job():
    print("child thread")
t=Thread(target=job)
print(t.isDaemon())
t.setDaemon(True)
print(t.isDaemon())


SYNCHRONISATION: 
muliple threads are executing simultaneously and have inconsistency problems
solution as synchronisation---" single thread ata time"
from threading import *
import time

def job(name):
    for i in range(10):
        print("child thread")
        time.sleep(2)
        print(name)
t=Thread(target=job,args=("sony",))
t1=Thread(target=job,args=("smitha",))
t.start()
t1.start()


SYNCHRONISATION by lock 
lock()
release()

from threading import *
import time
l=Lock()
def job(name):
    l.acquire()
    for i in range(10):
        print("child thread")
        time.sleep(2)
        print(name)
    l.release()

    
t=Thread(target=job,args=("sony",))
t1=Thread(target=job,args=("smitha",))
t.start()
t1.start()

# only one thread is allowed to exxecute 




SYNCHRONISATION by Rlock
r-reentrant
thread can acquire same lock again and again 
owner thread available


INTER THREAD COMMUNICATIONS:
producer and consumer communication
event condittion queue

INTER THREAD COMMUNICATION using event:
event obj
e=threading.Event()
event manages an internal flags set and clear

set()- green signal
clear()- red signal
isSet()- checks event is set or not
wait(sec)- wait event

INTER THREAD COMMUNICATION by condition
advanced
cond= threading.Condition()
acquire()
release()
wait(time)
notify()
notifyAll()

INTER THREAD COMMUNICATION by queue

q=queue.Queue()
put()
get()

types()
fifo
lifo
priority
  





 REGULAR EXPRESSIONS

if we want to represent a group of string in particular format we use regular expressions
they are declarative mechanisms to represent a string

example we can represent a phone numbers 

APPLICATIONS:
framework or validation logic
pattern matching applications
traslators
digital circuits
communication protocols


module: re

import re

compile()-- convert pattern to regexobject
finditer()- matches object

import re
count=0
p=re.compile("ab")
m=p.finditer("abaababa")
for m1 in m:
    count=count+1
    print(m1.start(),m1.end(),m1.group())
print("occurances",count)


import re
count=0
m=re.finditer("ab","abaababa")
for m1 in m:
    count=count+1
    print(m1.start(),m1.end(),m1.group())
print("occurances",count)

regex classes:
[abc]--- a or b or c
[^abc]---- except a and b and c
[a-z]- 
[A-Z]
[a-zA-Z]
[0-9]
[a-zA-Z0-9]
[^a-zA-Z0-9]

import re
m=re.search(r'[a-z]',"affdtyuu")
print(m)


predefined char:
\s- space char
\S- except space bar
\d- digits
\D- except digits
\w- word
\W- except words
. - special char including

QUANTIFIER
a- exact one a
a+- atleast one a
a*- any no including zero
a?- either 0 or 1 
a{n}- exact n no of a's
a{m,n}- min m to max n of a 



SOME IMPORTANT METHODS:

match():--- to check pattern at beggining of target string

import re
re.match("abbbbb","abbbbabbbbabbbba")


fullmatch()-- import re
re.fullmatch("ab","ab")


search()-- availabale or not

import re
re.search("ab","abhfhgsggdyuab")


findall()- occurances

finditer()- uield match chevking

sub()- substitution replacement
import re
re.sub("[a-z]","#","anjuihvkjnk128754f@$%%az6")



subn()-- 


split()-- 

^ symbol--- 
$ symbol--- 




WEB SCRAPING:
import re
import urllib
import urllib.request

sites="google rediff".spilt()
print(sites)

for s in sites:
print("searching ",s)

u=urllib.request.urlopen("http://"+s+".com")
text=u.read()

t= re.findall(str(text))




DECORATOR:  is a function in which we can take a function as arguments and extends its functionality 
and returns modified function with extended functionality


def wish():
print("hello sunil welcome")

wish()


@decor
def wish(name):
print("hello ",name,"welcome home")

wish(sunil)
wishvarma)
wish(nanda)




GENARATOR: generator is a function which is responsible to generate sequence of values

yield 


def mygen():
yield 'a'
yield 'b'
yield 'c'
yield 'd'

g=mygen()
print(type(g))

print(next(g))
print(next(g))
print(next(g))
print(next(g))
print(next(g))


adv:
class level iterators
memory utilisation and performance
web scraping and crawling


ASSERTION: debbuging 
2 tpes 
simple version: assert cond_expression

agrumented version : assert cond_expression, message


def s(x):
return x*x

assert s(2)==4," square value is 4"
assert s(3)==9," square value is 9"


LOGGING:

high recommended to stor complete info of app flow and exception infor to a file 
debugging
statistic provide


CRITICAL->50-- very serious problem and need attention
ERROR->40---SERIOUS ERRORS
WARNING->30---CAUTIONS
INFO->20 --- IMP MESSAGE
DEBUG->10 
NOTSET->0 - LEVEL IS NOT SET


import logging
logging.basicconfig()
logging.dubug("")
logging.info("")
logging.warning("")
logging.error("")
logging.crirical("")



GUI - GRAPHICAL USER INTERFACE
STEPS

1. import tkinter module
2. create top level window
3. add widgets to top level window
4. pack - limitations
5. mainloop()- 


import tkinter
or from tkinter import 
or import tkinter as t



Enter password: ****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.28 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database f1;
Query OK, 1 row affected (0.65 sec)

mysql> ^C
mysql> show databases;
+-------------------------+
| Database                |
+-------------------------+
| f1                      |
| information_schema      |
| javasession_db_shearise |
| mydb                    |
| mysql                   |
| performance_schema      |
| practice                |
| sakila                  |
| sys                     |
| world                   |
+-------------------------+
10 rows in set (0.30 sec)

mysql> use f1;
Database changed
mysql> create database f1;
ERROR 1007 (HY000): Can't create database 'f1'; database exists
mysql> delete database f1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database f1' at line 1
mysql> drop database f1;
Query OK, 0 rows affected (0.45 sec)

mysql> show databases;
+-------------------------+
| Database                |
+-------------------------+
| information_schema      |
| javasession_db_shearise |
| mydb                    |
| mysql                   |
| performance_schema      |
| practice                |
| sakila                  |
| sys                     |
| world                   |
+-------------------------+
9 rows in set (0.00 sec)

mysql> create database session;
Query OK, 1 row affected (0.20 sec)

mysql> show databases;
+-------------------------+
| Database                |
+-------------------------+
| information_schema      |
| javasession_db_shearise |
| mydb                    |
| mysql                   |
| performance_schema      |
| practice                |
| sakila                  |
| session                 |
| sys                     |
| world                   |
+-------------------------+
10 rows in set (0.00 sec)

mysql> use session;
Database changed
mysql> create table student(id int NOT NULL AUTO_INCREMENT,
    -> name varchar(20),
    -> age int);
ERROR 1075 (42000): Incorrect table definition; there can be only one auto column and it must be defined as a key
mysql> create table student(id int NOT NULL AUTO_INCREMENT,
    -> name varchar(20),
    -> age int,PRIMARY KET(id));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'KET(id))' at line 3
mysql> create table student(id int NOT NULL AUTO_INCREMENT,
    -> name varchar(20),
    -> age int,PRIMARY KEY(id));
Query OK, 0 rows affected (2.14 sec)

mysql> show tables;
+-------------------+
| Tables_in_session |
+-------------------+
| student           |
+-------------------+
1 row in set (0.22 sec)

mysql> describe student;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| id    | int         | NO   | PRI | NULL    | auto_increment |
| name  | varchar(20) | YES  |     | NULL    |                |
| age   | int         | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
3 rows in set (0.02 sec)

mysql> insert into student(id,name,age) values(1,"peter",588)
    -> insert into student(id,name,age) values(1,"peter",588);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'insert into student(id,name,age) values(1,"peter",588)' at line 2
mysql> insert into student(id,name,age) values(1,"peter",588);
Query OK, 1 row affected (0.23 sec)

mysql> insert into student(id,name,age) values(2,"pe12ter",188);
Query OK, 1 row affected (0.18 sec)

mysql> show tables;
+-------------------+
| Tables_in_session |
+-------------------+
| student           |
+-------------------+
1 row in set (0.02 sec)

mysql> select * from student;
+----+---------+------+
| id | name    | age  |
+----+---------+------+
|  1 | peter   |  588 |
|  2 | pe12ter |  188 |
+----+---------+------+
2 rows in set (0.00 sec)

mysql>











import cx_Oracle
try:
    con=cx_Oracle.connect('scott/tiger@localhost')
    c=con.cursor()
    c.execute("create table student(id int,namr varchar(20)")
    print("success")
except cx.Oracle.DatabaseError as e:
    if con:
        con.rollback()
        print(e)
finally:
    if cursor:
        cursor.close()
    if con:
        con.close()
        


















