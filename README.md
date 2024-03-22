# OmSakthi-Software
Developed a Sale order Billing application software. Using Angular for the front end, Spring Boot for the backend, with MySQL database Project has user management, Vendor management and Invoice management. Project has user management, Vendor management and Invoice management. In user management includes User and roll creation, Login Authentication. Vendor management includes Vendor Creation, update, and delete. Invoice management includes Invoice Create, updating, and delete.

database for mysql

create database omsakthi;
use omsakthi;
show tables;
 create table VENDOR(
 Id int not null AUTO_INCREMENT,
 VENDORNAME varchar (50),
 GSTNUMBER varchar (50) UNIQUE,
 PAN VARCHAR(50),
 ADDRESSLINE1 varchar(50),
 ADDRESSLINE2 varchar(50),
 CITY varchar(50),
 STATE varchar(50),
 PINCODE varchar(10),
 COUNTRY varchar(50),
 PHONENUMBER varchar(14),
 PRIMARY KEY (id)
 );
 
 select * from vendor;
 
create table INVOICE(
 INVOICEID int not null AUTO_INCREMENT,
 INVOICENUMBER varchar (50) UNIQUE,
 INVOICEDATE varchar (50) ,
 VENDORID INTEGER,
 TAX decimal(6,2),
 TOTALAMOUNT INTEGER,
 CGST INTEGER,
 SGST INTEGER,
 PRIMARY KEY (INVOICEID),
   FOREIGN KEY (VENDORID) REFERENCES VENDOR(Id)
 );
 ALTER TABLE INVOICE
MODIFY COLUMN TOTALAMOUNT int;
desc  invoice;
create table PARTICULAR(
 ID int not null AUTO_INCREMENT,
 INVOICENUMBER varchar (50),
 ITEM varchar (50) ,
 HSN_SAC varchar(50),
 QUANTITY varchar(10),
 RATE DECIMAL(6,2),
 TOTALPRICE integer,
 PRIMARY KEY (ID),
 FOREIGN KEY (INVOICENUMBER)
 REFERENCES INVOICE (INVOICENUMBER)
 );

create table user(
id int not null primary key auto_increment,
username varchar(20),
email varchar(50),
password varchar(120));

create table roles(
id int not null primary key auto_increment,
name varchar(20));

create table user_roles(
user_id bigint(20) primary key,
role_id int(11));
select * from user;
select * from user_roles;
INSERT INTO roles (`id`,`name`) VALUES (1,'ROLE_USER');
INSERT INTO roles (`id`,`name`) VALUES (2,'ROLE_MODERATOR');
INSERT INTO roles(`id`,`name`) VALUES (3,'ROLE_ADMIN');

 sample json for invoice
 {
    "invoiceNumber": "2",
    "invoiceDate": "Mani@1234",
    "vendorId": "2",
    "totalAmount": "200",
    "cgst": "9",
    "sgst": "9",
    "particulars": [
        {
            "item": "apple",
            "hsnsac":"hsnsac",
            "quantity": "1",
            "rate":"5"
        },
        {
            "item": "mango",
            "hsnsac":"hsnsac2",
            "quantity": "2",
            "rate":"10"
        }
    ]
}
json for vendor
{
    "vendorName":"vendorName",
    "gstNo":"gstNo",
    "panNo":"panNo",
    "address1":"address1",
     "address2":"address2",
     "city":"city",
     "state":"state",
     "pinCode":"pinCode",
     "contry":"contry",
    "phoneNumber":"887015586"
    
}


