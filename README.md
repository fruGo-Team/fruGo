# **_fruGo_**

## **R1: Description of website**

---

## **Concept**

fruGo is an online fresh produce ordering & delivery company that has been providing Australians with their fruit and vegetables since 2003. With several family owned merchant businesses and dispatch facilities in each major city of the country, fruGo has enjoyed being Australia’s most trusted whole food supplier for two decades.
Originally trading as a phone-order service with a proud emphasis on customer relationships, recent rapid growth in demand due to the COVID pandemic has prompted a major upgrade and overhaul of their web marketplace to reflect today’s digital shopping landscape and offer our customers a modernised and improved user experience.
When the world was forced into a predominantly online market in early 2020, fruGo faced challenges competing with other large supermarket chains that offered delivery due to their scale and convenience, however once our new vision of a purely web-based delivery powerhouse is realised, fruGo is confident that it will once again lead the market as Australia’s fresh food supplier.

## **Purpose**

The purpose of building a new online platform for fruGo is to utilise modern technologies to improve the reliability and delivery performance for customers and merchants alike.
Previously, customers would manually choose which merchant to order from and place orders on the telephone. fruGo believes that a successful business is an efficient one, so this process will be streamlined with the use of an online commerce platform using third-party services to automatically evaluate the closest merchant able to fulfil their particular order, enhancing the process for everyone.
Customers can also instantly view product quantities across various merchants in their city to reduce stock issues.
Merchants can now manage their stock quantities in an online database, which is automatically updated by customer orders, reducing the need for manual stocktakes and customer enquiries.

## **R2: Dataflow Diagram**

## **R3: Application Architecture Diagram**

![Application Architecture Diagram](./docs/AAD.png)

## **R4: User Stories**

**_As the owner/admin of the fruGo company, I would like:_**

[ ] To have full control (all CRUD functionality) over 'customers' & 'merchants', so that unwanted users can be removed and unexpected errors can be handled.

[ ] **_Merchants_** can only be added by me, so that unwanted merchants aren't selling unapproved products

**_As a merchant of fruGo, I would like:_**

[ ] To view/edit my profile in order to provide accurate information my store

[ ] Each customer must be signed in order to view the available products

[ ] To **_update_** my current product availablity/stock, to make sure all products are up to date

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
