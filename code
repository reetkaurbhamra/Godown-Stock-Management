
import mysql.connector as ms
import datetime
import tkinter as tk 


now=datetime.datetime.now()

root=tk.Tk()
root.title('Godown Stock')

#Clearscreen 
def clrscr():
    print("\n"*5)


#ProductManagement 
def add_product():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", 
                    database="stock")
    mycursor=mydb.cursor()
    sql= "INSERT INTO product(pcode, pname, pprice,pqty, pcat) VALUES  
         (%s,%s,%s,%s,%s)"
    a=tk.Label(root, text='Enter Product Code').pack(side='left')
    z=tk.Entry(root).pack(side='left')
    code=z.get()
    search="SELECT count(*) FROM product WHERE pcode=%s;"
    val=(code)
    mycursor.execute(search,val)
    for x in mycursor:
        cnt=x[0]
        if cnt==0:
            c=tk.Label(root, text='Name:').pack(side='top')
            a=tk.Entry(root).pack(side='top')
            name=a.get()
            d=tk.Label(root, text='Quantity:').pack(side='top')
            b=tk.Entry(root).pack(side='top')
            qty=b.get()
            e=tk.Label(root, text='Price:').pack(side='top')
            f=tk.Entry(root).pack(side='top')
            price=f.get()
            g=tk.Label(root, text='Category:').pack(side='top')
            h=tk.Entry(root).pack(side='top')
            cat=h.get()   
            val=(code,name,price,qty,cat)
            mycursor.execute(sql,val)
            mydb.commit()
        else:
            s=tk.Label(root, text='Product Already Exists.').pack(side='top')
 
def list_product():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT * FROM product"
    mycursor.execute(sql)
    clrscr()
    a=tk.Label(root, text="Product Details").pack(side='top')
    b=tk.Label(root, text="Code Name Price Quantity Category").pack(side='top')
    for i in mycursor:
        print("\t\t",i[0],"\t",i[1],"\t",i[2],"\t",i[3],"\t",i[4])
        
def list_prcode():
    z=tk.Label(root, text="Enter product code:").pack(side='top')
    y=tk.Entry(root).pack(side='top')
    code=y.get()
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT* FROM product WHERE pcode=%s"
    val=(code,)
    mycursor.execute(sql,val)
    clrscr()
    a=tk.Label(root, text="Product Details").pack(side='top')
    b=tk.Label(root, text="Code Name Price Quantity Category").pack(side='top')
    for i in mycursor:
        print("\t\t",i[0],"\t",i[1],"\t",i[2],"\t",i[3],"\t",i[4])
        
def list_prcat():
    z=tk.Label(root, text="Enter category:").pack(side='top')
    y=tk.Entry(root).pack(side='top')
    cat=y.get()
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT* FROM product WHERE pcat=%s"
    val=(cat)
    mycursor.execute(sql,val)
    clrscr()
    a=tk.Label(root, text="Product Details").pack(side='top')
    b=tk.Label(root, text="Code Name Price Quantity Category").pack(side='top')
    for i in mycursor:
        print("\t\t",i[0],"\t",i[1],"\t",i[2],"\t",i[3],"\t",i[4])
              
def search_product():
    a=tk.Button(root,text='List All Product',command=list_product).pack(side='left')
    b=tk.Button(root,text='List Product Code Wise',command=list_prcode).pack(side='left')
    c=tk.Button(root,text='List All Product',command=list_prcat).pack(side='left')

def update_product():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    z=tk.Label(root, text="Enter the product code:").pack(side='top')
    y=tk.Entry(root).pack(side='top')
    code=y.get()
    a=tk.Label(root, text="Enter the quantity:").pack(side='top')
    b=tk.Entry(root).pack(side='top')
    qty=b.get()
    sql="UPDATE product SET pqty=pqty+%s WHERE pcode=%s;"
    val=(qty,code)
    mycursor.execute(sql,val)
    mydb.commit()
    d=tk.Label(root, text="Record(s) Updated")
    
def delete_product(): 
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    z=tk.Label(root, text="Enter the product code:").pack(side='top')
    y=tk.Entry(root).pack(side='top')
    code=y.get()
    sql="DELETE FROM product WHERE pcode=%s;"
    val=(code,)
    mycursor.execute(sql,val)
    print(mycursor.rowcount)
    d=tk.Label(root, text="Record(s) Deleted")
    
def product_mgmt():
    a=tk.Button(root,text='Add New Item',command=add_product).pack(side='left')
    b=tk.Button(root,text='List Item', command=search_product).pack(side='left')
    c=tk.Button(root,text='Update Item', command=update_product).pack(side='left')
    d=tk.Button(root,text='Delete Item',command=delete_product).pack(side='left')

#PurchaseManagement
def add_order():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    now=datetime.datetime.now()
    sql="INSERT INTO orders(oderid,orderdate,pcode,pprice,pqty,supplier,pcat) VALUES(%s,%s,%s,%s,%s,%s,%s)"
    z=tk.Label(root, text="Enter the product code:").pack(side='top')
    y=tk.Entry(root).pack(side='top')
    code=y.get()
    oid=now.year+now.month+now.day+now.hour+now.minute+now.second
    a=tk.Label(root, text="Enter the quantity:").pack(side='top')
    b=tk.Entry(root).pack(side='top')
    qty=b.get()
    c=tk.Label(root, text="Enter Product Unit Price:").pack(side='top')
    d=tk.Entry(root).pack(side='top')
    price=d.get()
    e=tk.Label(root, text="Enter Product Category:").pack(side='top')
    f=tk.Entry(root).pack(side='top')
    cat=f.get()
    g=tk.Label(root, text="Enter Supplier Details:").pack(side='top')
    h=tk.Entry(root).pack(side='top')
    supplier=h.get()
    val(oid,now,code,price,qty,supplier,cat)
    mycursor.execute(sql,val)
    mybd.commit()
    
def list_order():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor() 
    sql="SELECT * FROM ORDERS"
    mycursor.execute(sql)
    clrscr()
    a=tk.Label(root, text="ORDER DETAILS").pack(side='top')
    for i in mycursor:
        print("\t\t",i[0],"\t",i[1],"\t",i[2],"\t",i[3],"\t",i[4]) 

def purchase_management():
    a=tk.Button(root, text='Add Order', command=add_order).pack(side='top')
    b=tk.Button(root,text='List Order', command=list_order).pack(side='top')
 
#SalesManagement
def sale_item():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT count(*) FROM product WHERE pcode=%s;"
    val=(pcode,)
    mycursor.execute(sql,val)
    for x in mycursor:
        cnt=x[0]
        if c!=0:
            sql="SELECT * FROM product WHERE pcode=%s;"
            val=(pcode,)
            mycursor.execute(sql,val)
            for x in mycursor:
                a=tk.Label(root, text=x).pack()
                price=tk.Label(root, text=x[2]).pack()
                pqty=tk.Label(root, text=x[3]).pack()
                b=tk.Label(root, text="Enter no of quantity:").pack(side='top')
                c=tk.Entry(root).pack(side='top')
                qty=c.get()
                if qty <= pqty:
                    total=qty*price;
                    s=tk.Label(root, text="Collect Rs."+total).pack()
                    sql="INSERT INTO sales VALUES(%s,%s,%s,%s,%s,%s)"
                    val=(int(cnt)+1,datetime.datetime.now(),pcode(),price,qty,total)
                    mycursor.execute(sql,val)
                    mydb.commit()
                else:
                    w=tk.Label(root, text="Quantity not available").pack()
        else:
             t=tk.Label(root, text="Product is not available").pack()
             
def list_sale():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT * FROM sales"
    mycursor.execute(sql)
    a=tk.Label(root, text="SALES DETAILS").pack()
    b=tk.Label(root, text="Sales id Date Productcode Price Quantity Total").pack()
    for x in mycursor:
        r=tk.Label(root,   text=x[0]+"\t"+x[1]+"\t"+x[2]+"\t"+x[3]+"\t"+x[4]+"\t"+x[5]).pack()
    
def sales_management():
    a=tk.Button(root, text='Sale Items', command=sale_item).pack(side='top')
    b=tk.Button(root,text='List Sale', command=list_sale).pack(side='top')


#UserManagement
def add_user():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    a=tk.Label(root, text="Enter email ID:").pack(side='top')
    b=tk.Entry(root).pack(side='top')
    UID=b.get()
    c=tk.Label(root, text="Enter name:").pack(side='top')
    d=tk.Entry(root).pack(side='top')
    NAME=d.get()
    e=tk.Label(root, text="Enter Password:").pack(side='top')
    f=tk.Entry(root).pack(side='top')
    PASWD=f.get()
    sql="INSERT INTO user VAUES(%s,%s,%s);"
    VAL=(UID,NAME,PASWD)
    mycursor.execute(sql,val)
    mydb.commit()
    t=tk.Label(root, text=mycursor.rowcount+"user created").pack(side='top')
    
def list_user():    
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SELECT uid, uname FROM user"
    mycursor.execute(sql)
    clrscr()
    e=tk.Label(root, text="User Details").pack(side='top')
    f=tk.Label(root, text=i[0]+"\t"+i[1]).pack(side='top')
    
def user_management():
    a=tk.Button(root, text='Add User', command=add_user).pack(side='top')
    b=tk.Button(root,text='List User', command=list_user).pack(side='top')
 

#DatabaseSetup
def create_database():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    a=tk.Label(root, text="CREATING PRODUCT TABLE").pack(side='top')
    sql="CREATE TABLE if not exists product(pcodeint(4) PRIMARY KEY, pname CHAR(30) NOT NULL,pprice FLOAT(8,2),pqtyint(4), pcat CHAR(30))"
    mycursor.execute(sql)
    b=tk.Label(root, text="CREATING ORDER TABLE").pack(side='top')
    sql="CREATE TABLE if not exists orders(order int(4) PRIMARY KEY, orderdate DATE, pcode CHAR(30) NOT NULL, pprice FLOAT(8,2), pqtyint(4), supplier CHAR(30))"
    mycursor.execute(sql)
    c=tk.Label(root, text="ORDER table created").pack(side='top')
    sql="CREATE TABLE if not exists orders(order int(4) PRIMARY KEY, orderdate DATE, pcode CHAR(30) NOT NULL, pprice FLOAT(8,2), pqtyint(4), supplier CHAR(30))"
    mycursor.execute(sql) 
    d=tk.Label(root, text="Creating SALES Table").pack(side='top')
    sql="CREATE TABLE if not exists orders(salesid int(4) PRIMARY KEY, salesdate DATE, pcode CHAR(30) references product(pcode), pprice FLOAT(8,2), pqtyint(4), Total_double CHAR(30))"
    mycursor.execute(sql)
    e=tk.Label(root, text="Sales table created").pack(side='top')
    sql="CREATE TABLE if not exists user(uid int(4) PRIMARY KEY, uname CHAR(3O) NOT NULL, upwd CHAR(30))"
    mycursor.execute(sql)
    f=tk.Label(root, text="USER table created").pack(side='top') 
    
def list_database():
    mydb=ms.connect(host="localhost", user="root", passwd="reet1996", database="stock")
    mycursor=mydb.cursor()
    sql="SHOW TABLES"
    mycursor.execute(sql)
    for i in mycursor:
        a=tk.Label(root, text=i).pack(side='top')    

def db_mgmt():
    a=tk.Button(root, text='Database Creation', command=create_database).pack(side='top')
    b=tk.Button(root,text='List Database', command=list_database).pack(side='top')
        
        
#DRIVER_CODE    
a=tk.Label(root, text='GODOWN STOCK CONTROLLING').pack(side='top')
z=tk.Label(root, text='********************************************************\n').pack(side='top')
b=tk.Button(root,text='Product Management', command=product_mgmt, width=30).pack(side='top')
c=tk.Button(root, text='Purchase Management', command=purchase_management, width=30).pack(side='top')
d=tk.Button(root, text='Sales Management', command=sales_management, width=30).pack(side='top')
e=tk.Button(root, text='User Management', command=user_management, width=30).pack(side='top')
e=tk.Button(root, text='Database Setup', command=db_mgmt, width=30).pack(side='top')

root.mainloop()

