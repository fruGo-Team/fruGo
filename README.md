# **_*fruGo*_**

## **R1: Description of website**

### **Concept**

fruGo is an online fresh produce ordering & delivery company that has been providing Australians with their fruit and vegetables since 2003. With small family owned dispatch facilities in each major city of the country, fruGo has enjoyed being Australia’s most trusted whole food supplier for two decades.

Originally trading as a phone-order service with a proud emphasis on customer relationships, recent rapid growth in demand due to the COVID pandemic has prompted a major upgrade and overhaul of their web marketplace to reflect today’s digital shopping landscape and offer our customers a modernised and improved user experience.

When the world was forced into a predominantly online market in early 2020, fruGo faced challenges competing with other large supermarket chains that offered delivery due to their scale and convenience, however once our new vision of a purely web-based delivery powerhouse is realised, fruGo is confident that it will once again lead the market as Australia’s fresh food supplier.

### **Purpose**

The purpose of building a new online platform for fruGo is to utilise modern technologies to improve the reliability and delivery performance for customers and merchants alike.

Previously, customers would manually choose which merchant to order from and place orders via a telephone service. fruGo believes that a successful business is an efficient one, so this process will be streamlined with the use of an online commerce platform using automated processes to automatically evaluate the closest merchant able to fulfill their particular order, enhancing the process for everyone.

fruGo is passionate about the freshness of their produce and reducing food wastage, and we believe that the need to bulk-buy to reduce visits to physical grocery stores is depriving the public of truly fresh food. Not only do we aim to make ordering quick and stress-free, we have no delivery fee so that our customers can only order what they need, more frequently!

Prior to this update, Customers had to enter their personal details (such as delivery information) for every order. We will be introducing authentication/authorisation features so that users will have their information stored securely in an online account! Customers can also now instantly view product quantities in their respective city to reduce stock issues.
Merchants now have the ability manage their stock quantities in an online database, which is automatically updated by customer orders, reducing the need for manual stock-takes and customer enquiries.

### **Features & functionalities**

fruGo’s online platform is a dynamic website that will be built off of a REST API that interacts with a document-oriented database. The database will store various data entities as collections in a _MongoDB_ database, able to be interacted with and have various specified CRUD operations performed on them through _Mongoose_ Schema/models via _Express_ routes and logic controllers. This back-end logic will be accessed by users via an interactive front-end built with _React_.

The three external entities that will be interacting with the application are `Customers`, `Merchants` and `Admins`.

### `Admin`

**Actions:**

- View all non-sensitive data of customers/merchants
- View all orders and cancel/update if needed
- Add and remove products from merchant's stock
- Perform all other tasks other than view/update sensitive data

```js
Admin {
  _id: ObjectId, // Unique document identifier
  email: String, // Email address (validated)
  username: String, // Display name identifier
  password: String, // Password (min. 8 characters, stored as hash)
  firstName: String, // First name
  lastName: String, // Last name
}
```

### `Customer`

**Actions:**

- Create a customer profile with login credentials and personal information
- View their profile
- Update their details
- Delete their profile
- Add and remove items to their cart
- Submit their cart and create an order
- Search for products
- Filter products by type

**Data model:**

```js
Customer {
  _id: ObjectId, // Unique document identifier
  email: String, // Email address (validated)
  password: String, // Password (min. 8 characters, stored as hash)
  username: String, // Display name identifier
  firstName: String, // First name
  lastName: String, // Last name
  city: ObjectId, // Referenced City object
  streetAddress: String, // Street address for delivery
  orders: Array, // Referenced Order objects
}
```

### `Merchant`

**Actions:**

- View their profile
- Update their profile details
- View their stock/product quantities
- Update their stock quantities
- Add and remove products from their inventory
- View their pending and completed orders
- Cancel their orders

**Data model:**

```js
Merchant {
  _id: ObjectId, // Unique document identifier
  email: String, // Email address (validated)
  password: String, // Password (min. 8 characters, stored as hash)
  username: String, // Display name identifier
  name: String, // Business name
  description: String, // Brief description of business
  city: ObjectId, // Referenced City object
  streetAddress: String, // Street address for delivery,
  stock: Array, // Referenced StockProduct objects (includes product and stock quantity)
  orders: Array, // Referenced Order objects
}
```

The data models that these external entities will be interacting with are `Products`, `StockProduct`, `Carts`, `Orders` & `Cities`.

### `Product`

**Data model:**

```js
Product {
  _id: ObjectId, // Unique document identifier
  name: String, // Name of food product
  type: String, // Type of food product
  price: Number, // Price of food product
}
```

### `StockProduct`

**Data model:**

```js
StockProduct {
  _id: ObjectId, // Unique document identifier
  merchant: ObjectId, // Referenced Merchant object
  product: ObjectId, // Referenced Product object
  quantity: Number, // Current quantity Merchant has in stock
}
```

### `Cart`

**Data model:**

```js
Cart {
  _id: ObjectId, // Unique document identifier
  customer: ObjectId, // Referenced Customer object
  merchant: ObjectId, // Referenced Merchant object
  products: Array, // Array of objects storing Product object & quantity
  totalPrice: Number, // Current total price in AUD
}
```

### `Order`

**Data model:**

```js
Order {
  _id: ObjectId, // Unique document identifier
  cart: ObjectId, // Referenced Cart object
  timestamps: true, // Will add createdAt & updatedAt properties by default
  createdAt: Date, // Date object of creation timestamp
  updatedAt: Date, // Date object of any update timestamps
  status: String, // "pending" (default), "complete", "cancelled"
}
```

### `City`

**Data model:**

```js
City {
  _id: ObjectId, // Unique document identifier
  name: String, // Name of major city
}
```

### **Target audience**

**Income level**: Middle to upper-middle class  
**Location**: Metropolitan areas in Australian major cities  
**Age**: 25-34 years old  
**Occupation**: Busy full-time employees with little time to visit grocery store  
**Education** level: Moderately educated individuals with a decent understanding of modern technology  
**Language**: English  
**Gender**: All  
**Devices**: Smart phone (iOS & Android), tablets, desktop  
**Motivation**: To simplify and streamline buying fresh food so that they have more free time  
**Needs**:

- An easy to understand and straight-forward user interface
- Clear pricing
- Ability to modify their cart
- Location-based merchant selection for rapid delivery
- Visibility for merchants

### **Tech stack**

**Languages**: `JavaScript`, `HTML`, `CSS`  
**Database:** `MongoDB`  
**Object Data Mapping (ODM):** `Mongoose`  
**Web framework:** `Express`  
**User interface libraries:** `React`, `styled components`, `mui`  
**JS server environment:** `Node.js`, `nodemon`  
**Encryption/decryption:** `CryptoJS`  
**Hashing/salt:** `bcrypt`  
**Access tokens:** `JsonWebToken`  
**Testing:** `Jest`, `supertest`  
**Routing:** `React Router DOM`  
**HTTP client:** `Axios`  
**HTTP header security:** `Helmet.js`  
**Resource management:** `cors`

## **R2: Dataflow Diagrams**

### **Level 0: Order Products**

![L0 Order Products](./docs/diagrams/l0-order-products.png)

### **Level 1: Order Products**

![L1 Order Products](./docs/diagrams/l1-order-products.png)

## **R3: Application Architecture Diagram**

![Application Architecture Diagram](./docs/diagrams/AAD.png)

## **R4: User Stories**

**_As the owner/admin of the fruGo company, I would like:_**

[ ] To have full control (all CRUD functionality) over 'customers' & 'merchants', so that unwanted users can be removed and unexpected errors can be handled.

[ ] **_Merchants_** can only be added by me, so that unwanted merchants aren't selling unapproved products

**_As a merchant of fruGo, I would like:_**

[ ] To view/edit my profile in order to provide accurate information relating to my store

[ ] Each customer must be signed in order to view the available products

[ ] To **_update_** my current product availability/stock, to make sure all products are up to date

[ ] **_Add/Create_** new products to my store, to keep up with customer demand

[ ] **_Delete_** any of my product listings (if needed), so that customers aren't purchasing unavailable products

[ ] To view both 'pending' and 'completed' orders

[ ] Delete 'pending' orders if stock isn't available in order to notify users that their order was unsuccessful (with the provided reason)

[ ] To mark pending orders from customers as completed to notify customers that their order was successful

[ ] Every completed **_ORDER_** by a customer to be sent to me, in order to keep receipts of all transactions

[ ] Completed orders to update the stock of the purchased products, in order to communicate to customers how much stock is left

**_As a customer of fruGo, I would like:_**

[ ] To create an account in order to store my information for future orders and save past orders as well

[ ] Edit my account information so that it's up to date, and the option to delete my account in not needed anymore

[ ] To have a Sign in/Sign up Page, in order to ensure online user authentication

[ ] To only view products that are available in my city, in order get the fastest delivery possible

[ ] To search for products, in order find them quickly without scrolling through all products at once

[ ] Filter products by type, to enhance the searching experience

[ ] Add desired products to a temporary cart in order to keep shopping until I'm ready to finalise my order

[ ] Remove products from a cart in case I don't want them anymore

## **R5: fruGo Wireframes**

### **_1A (PC) - Homepage (NOT Signed In)_**

![1A (PC) - Homepage (NOT Signed In)](<./docs/wireframes/1A%20(PC)%20-%20Homepage%20(NOT%20Signed%20In).png>)

### **_1B (Mobile) - Homepage (NOT Signed In)_**

![1B (Mobile) - Homepage (NOT Signed In)](<./docs/wireframes/1B (Mobile) - Homepage (NOT Signed In).png>)

### **_2A (PC) - Products Page (NOT Signed In)_**

![2A (PC) - Products Page (NOT Signed In)](<./docs/wireframes/2A (PC) - Products Page (NOT Signed In).png>)

### **_2B (Mobile) - Products Page (NOT Signed In)_**

![2B (Mobile) - Products Page (NOT Signed In)](<./docs/wireframes/2B (Mobile) - Products Page (NOT Signed In).png>)

### **_3A (PC) - Sign In Page (ALL Users)_**

![3A (PC) - Sign In Page (ALL Users)](<./docs/wireframes/3A (PC) - Sign In Page (ALL Users).png>)

### **_3B (Mobile) - Sign In Page (ALL Users)_**

![3B (Mobile) - Sign In Page (ALL Users)](<./docs/wireframes/3B (Mobile) - Sign In Page (ALL Users).png>)

### **_4A (PC) - Customer Homepage_**

![4A (PC) - Customer Homepage](<./docs/wireframes/4A (PC) - Customer Homepage.png>)

### **_4B (Mobile) - Customer Homepage_**

![4B (Mobile) - Customer Homepage](<./docs/wireframes/4B (Mobile) - Customer Homepage.png>)

### **_5A (PC) - Customer Products Page_**

![5A (PC) - Customer Products Page](<./docs/wireframes/5A (PC) - Customer Products Page.png>)

### **_5B (Mobile) - Customer Products Page_**

![5B (Mobile) - Customer Products Page](<./docs/wireframes/5B (Mobile) - Customer Products Page.png>)

### **_6A (PC) - Customer Cart Page_**

![6A (PC) - Customer Cart Page](<./docs/wireframes/6A (PC) - Customer Cart Page.png>)

### **_6B (Mobile) - Customer Cart Page_**

![6B (Mobile) - Customer Cart Page](<./docs/wireframes/6B (Mobile) - Customer Cart Page.png>)

### **_7A (PC) - Customer Order Confirmation Page_**

![7A (PC) - Customer Order Confirmation Page](<./docs/wireframes/7A (PC) - Customer Order Confirmation Page.png>)

### **_7B (Mobile) - Customer Order Confirmation Page_**

![7B (Mobile) - Customer Order Confirmation Page](<./docs/wireframes/7B (Mobile) - Customer Order Confirmation Page.png>)

### **_8A (PC) - Customer Completed Orders_**

![8A (PC) - Customer Completed Orders](<./docs/wireframes/8A (PC) - Customer Completed Orders.png>)

### **_8B (Mobile) - Customer Completed Orders_**

![8B (Mobile) - Customer Completed Orders](<./docs/wireframes/8B (Mobile) - Customer Completed Orders.png>)

### **_9A (PC) - Merchant Homepage_**

![9A (PC) - Merchant Homepage](<./docs/wireframes/9A (PC) - Merchant Homepage.png>)

### **_9B (Mobile) - Merchant Homepage_**

![9B (Mobile) - Merchant Homepage](<./docs/wireframes/9B (Mobile) - Merchant Homepage.png>)

### **_10A (PC) - Merchant Products Page_**

![10A (PC) - Merchant Products Page](<./docs/wireframes/10A (PC) - Merchant Products Page.png>)

### **_10B (Mobile) - Merchant Products Page_**

![10B (Mobile) - Merchant Products Page](<./docs/wireframes/10B (Mobile) - Merchant Products Page.png>)

### **_11A (PC) - Merchant Add Product Page_**

![11A (PC) - Merchant Add Product Page](<./docs/wireframes/11A (PC) - Merchant Add Product Page.png>)

### **_11B (Mobile) - Merchant Add Product Page_**

![11B (Mobile) - Merchant Add Product Page](<./docs/wireframes/11B (Mobile) - Merchant Add Product Page.png>)

### **_12A (PC) - Merchant Orders_**

![12A (PC) - Merchant Orders](<./docs/wireframes/12A (PC) - Merchant Orders.png>)

### **_12B (Mobile) - Merchant Orders_**

![12B (Mobile) - Merchant Orders](<./docs/wireframes/12B (Mobile) - Merchant Orders.png>)

### **_13A (PC) - Admin Homepage_**

![13A (PC) - Admin Homepage](<./docs/wireframes/13A (PC) - Admin Homepage.png>)

### **_13B (Mobile) - Admin Homepage_**

![13B (Mobile) - Admin Homepage](<./docs/wireframes/13B (Mobile) - Admin Homepage.png>)

### **_14A (PC) - Admin/Merchant List_**

![14A (PC) - Admin/Merchant List](<./docs/wireframes/14A (PC) - Admin_Merchant List.png>)

### **_14B (Mobile) - Admin/Merchant List_**

![14B (Mobile) - Admin_Merchant List](<./docs/wireframes/14B (Mobile) - Admin_Merchant List.png>)

### **_15A (PC) - Admin/Add Merchant_**

![15A (PC) - Admin/Add Merchant](<./docs/wireframes/15A (PC) - Admin_Add Merchant.png>)

### **_15B (Mobile) - Admin/Add Merchant_**

![15B (Mobile) - Admin_Add Merchant](<./docs/wireframes/15B (Mobile) - Admin_Add Merchant.png>)

### **_16A (PC) - Admin/Update Merchant_**

![16A (PC) - Admin/Update Merchant](<./docs/wireframes/16A (PC) - Admin_Update Merchant.png>)

### **_16B (Mobile) - Admin/Update Merchant_**

![16B (Mobile) - Admin_Update Merchant](<./docs/wireframes/16B (Mobile) - Admin_Update Merchant.png>)

### **_17A (PC) - Admin/Customer List_**

![17A (PC) - Admin/Customer List](<./docs/wireframes/17A (PC) - Admin_Customer List.png>)

### **_17B (Mobile) - Admin/Customer List_**

![17B (Mobile) - Admin_Customer List](<./docs/wireframes/17B (Mobile) - Admin_Customer List.png>)

### **_18A (PC) - Register Page (CUSTOMERS ONLY)_**

![18A (PC) - Register Page (CUSTOMERS ONLY)](<./docs/wireframes/18A (PC) - Register Page (CUSTOMERS ONLY).png>)

### **_18B (Mobile) - Register Page (CUSTOMERS ONLY)_**

![18B (Mobile) - Register Page (CUSTOMERS ONLY)](<./docs/wireframes/18B (Mobile) - Register Page (CUSTOMERS ONLY).png>)
