# 💊 SmartPharma – Wholesale Pharmacy Management System

## 📌 Project Overview

SmartPharma is a Wholesale Pharmacy Management System developed using SAP ABAP 7.4. The project is designed to manage important wholesale pharmacy operations such as Customer Management, Vendor Management, Purchase Management, Sales and Billing, and Inventory/Stock Management.

The application uses custom SAP database tables, selection screens, ALV reports, and a Smart Form-based billing system to provide an integrated pharmacy management solution.

## 🎯 Objectives

- Manage wholesale pharmacy customer information.
- Maintain vendor details.
- Record medicine purchases.
- Manage medicine sales and billing.
- Track medicine stock and batch information.
- Monitor medicine expiry dates.
- Generate ALV-based reports.
- Generate customer invoices using SAP Smart Forms.
- Maintain sales and purchase history.
- Reduce duplicate customer records using mobile-number-based identification.

## 🛠️ Technologies Used

- SAP ABAP 7.4
- SAP GUI
- Eclipse ADT
- SAP HANA
- SE11
- ABAP Open SQL
- ALV using CL_SALV_TABLE
- SAP Smart Forms
- Selection Screens
- Custom Z Tables

## 📂 Main Program

Program Name: `ZSMARTPHARMA`

Transaction Code: `ZSP`

The main program provides a menu-driven selection screen through which users can access different modules of the application.

## 📋 Modules

### 1. Customer Management

The Customer Management module is used to maintain wholesale pharmacy customer information.

Functions:
- Display customer records
- Search customer records
- Create new customers
- Maintain customer contact details
- Store GST information
- Maintain customer type
- Track customer purchase history

Customer Table:

`ZSP_CUSTOMER`

Important fields:
- CUSTOMER_ID
- CUSTOMER_NAME
- CONTACT_PERSON
- MOBILE
- GST_NUMBER
- ADDRESS
- CUSTOMER_TYPE
- CREATED_ON

### 2. Vendor Management

The Vendor Management module maintains medicine supplier information.

Functions:
- Display vendors
- Create vendors
- Maintain vendor contact information
- Store GST details
- Maintain vendor address

Vendor Table:

`ZSP_VENDOR`

### 3. Purchase Management

The Purchase Management module records medicines purchased from vendors.

Functions:
- Display purchase records
- Display purchase details
- Create purchase transactions
- Store medicine batch numbers
- Maintain purchase quantity
- Maintain purchase price
- Maintain sales price

Purchase Tables:

`ZSP_PURCHASE_HDR`

`ZSP_PURCH_ITEM`

Purchase Structure:

Purchase Header  
→ Purchase Item 1  
→ Purchase Item 2  
→ Purchase Item 3

### 4. Sales and Billing

The Sales and Billing module handles customer medicine purchases.

The billing process first checks the customer's mobile number. If the customer already exists, the existing customer information is reused instead of creating a duplicate customer record. If the customer is new, the required customer information is created.

Billing Process:

Customer Mobile Number  
↓  
Check Customer  
↓  
Existing Customer / New Customer  
↓  
Reuse Customer / Create Customer  
↓  
Select Medicines  
↓  
Check Stock  
↓  
Calculate Total  
↓  
Save Sales Data  
↓  
Update Stock  
↓  
Generate Invoice

Sales Tables:

`ZSP_SALES_HDR`

`ZSP_SALES_ITEM`

### 5. Stock Management

The Stock Management module maintains current medicine inventory.

Functions:
- Display all stock
- Identify low-stock medicines
- Identify near-expiry medicines
- Identify expired medicines
- Maintain medicine batch numbers
- Track available quantity
- Maintain purchase and sales prices
- Track expiry dates

Stock Table:

`ZSP_INV_STOCK`

Important fields:
- MATNR
- BATCH_NO
- QUANTITY
- UNIT
- PURCHASE_PRICE
- SALES_PRICE
- EXPIRY_DATE
- UPDATED_ON

## 📊 ALV Reports

The application uses ABAP ALV for displaying application data.

The project uses:

`CL_SALV_TABLE`

ALV reports are provided for different modules including:

- Customer Report
- Vendor Report
- Purchase Report
- Sales Report
- Stock Report
- Stock Dashboard

ALV provides standard SAP features such as:

- Sorting
- Filtering
- Searching
- Column optimization
- Export functionality
- Layout management

## 🧾 Smart Form Invoice

The project uses SAP Smart Forms to generate customer invoices.

Smart Form:

`ZSF_SMARTPHARMA_BILL`

The Smart Form receives billing information such as:

- Bill Number
- Bill Date
- Customer ID
- Customer Name
- Mobile Number
- GST Number
- Address
- Total Amount
- Medicine Items

Bill Item Structure:

`ZST_SP_BILL_ITEM`

Table Type:

`ZTT_SP_BILL_ITEM`

The Smart Form generates an invoice preview after successful billing.

## 🗄️ Database Tables

The project uses custom SAP Z tables:

- `ZSP_CUSTOMER` – Customer master data
- `ZSP_VENDOR` – Vendor master data
- `ZSP_PURCHASE_HDR` – Purchase header
- `ZSP_PURCH_ITEM` – Purchase item details
- `ZSP_SALES_HDR` – Sales header
- `ZSP_SALES_ITEM` – Sales item details
- `ZSP_INV_STOCK` – Inventory and stock data

## 🔄 Application Flow

START  
↓  
ZSMARTPHARMA  
↓  
Main Menu Screen  
↓  
Customer / Vendor / Purchase / Sales & Billing / Stock  
↓  
ALV Reports  
↓  
Smart Form Invoice  
↓  
END

## 💾 Database Processing

The application performs database operations using ABAP Open SQL.

Database operations include:

- SELECT
- INSERT
- UPDATE
- MODIFY
- DELETE
- COMMIT WORK

Transactions are committed after successful billing and stock processing.

## ✅ Validations

The application performs validations such as:

- Customer mobile number validation
- Customer existence checking
- Vendor validation
- Medicine stock availability checking
- Batch validation
- Quantity validation
- Sales quantity validation
- Required customer information validation
- Stock quantity update after sale
- Duplicate customer prevention

## 🔐 Data Integrity

The system maintains consistency between customer, sales, sales items, and stock data.

Customer  
↓  
Sales  
↓  
Sales Items  
↓  
Stock

When medicines are sold, the corresponding stock quantity is reduced.

## 🧪 Testing

### Customer Testing

Create New Customer  
↓  
Save Customer  
↓  
Display Customer  
↓  
Verify ALV Output

### Purchase Testing

Create Purchase  
↓  
Enter Medicine  
↓  
Enter Batch  
↓  
Enter Quantity  
↓  
Save Purchase  
↓  
Verify Purchase Data

### Billing Testing

Enter Customer Mobile  
↓  
Check Existing Customer  
↓  
Enter Medicine  
↓  
Check Stock  
↓  
Calculate Bill  
↓  
Save Sales Data  
↓  
Update Stock  
↓  
Generate Smart Form

## 📁 Project Structure

SmartPharma

├── ZSMARTPHARMA

├── ZSP_CUSTOMER

├── ZSP_VENDOR

├── ZSP_PURCHASE_HDR

├── ZSP_PURCH_ITEM

├── ZSP_SALES_HDR

├── ZSP_SALES_ITEM

├── ZSP_INV_STOCK

├── ZST_SP_BILL_ITEM

├── ZTT_SP_BILL_ITEM

└── ZSF_SMARTPHARMA_BILL

## 🚀 Future Enhancements

Possible future improvements include:

- Barcode scanning
- Medicine master management
- Automatic stock replenishment
- Payment tracking
- GST calculation
- Advanced dashboard
- User authorization and roles
- Email invoice functionality
- PDF invoice generation
- Expiry notifications
- Advanced analytics
- Integration with standard SAP MM/SD processes

## 🎓 Project Type

Academic / Mini Project

Domain:

- Pharmacy Management
- Enterprise Resource Planning
- SAP ABAP
- Inventory Management
- Sales and Billing

## 👨‍💻 Developer

## Shaik Mahamood Anzar

B.Tech – Computer Science / Data Science

Interests:
- SAP ABAP
- Software Development
- Data Analytics
- Enterprise Applications

## ⭐ Key Highlights

- Developed using SAP ABAP 7.4
- Custom SAP Z tables
- Menu-driven application
- Customer and vendor management
- Purchase management
- Sales and billing
- Batch-wise stock management
- Expiry-date tracking
- ALV reporting
- SAP Smart Form invoice generation
- Customer history management
- Database transaction processing

## 📌 Conclusion

SmartPharma – Wholesale Pharmacy Management System demonstrates how SAP ABAP can be used to develop an integrated business application for managing pharmacy operations.

The project combines custom database tables, ABAP programming, selection screens, ALV reports, database operations, stock management, sales processing, and Smart Forms into a single SAP-based application.

## 📜 License

This project is developed for educational and academic purposes.
