## Anomaly Analysis

## Insert Anomaly
In the current denormalized dataset, product information (e.g., product_id, product_name) is stored along with order and customer details (order_id, order_date, customer_id).
This creates an insert anomaly where a new product cannot be added to the system unless it is associated with an order.
For example, if a new product is introduced but has not yet been ordered, there is no way to store its details without creating a dummy order entry.
This leads to incomplete data representation and forces invalid data entry.

## Update Anomaly
The dataset stores redundant customer, product, and sales representative information across multiple rows.
For example, if a customer's details such as customer_city or customer_email change, the update must be applied to multiple rows where that customer_id appears.
If some rows are missed during the update, it leads to inconsistent data.
Similarly, if product details like unit_price or category change, all corresponding rows must be updated.
This results in unreliable and inconsistent data due to partial updates.

## Delete Anomaly
In the current structure, deleting a single order record may result in the loss of important information about customers, products, and sales representatives.
For example, if a customer_id appears only once in the dataset and that order is deleted, all associated details such as customer_name, customer_email, and customer_city are also lost.
Similarly, deleting the only order containing a specific product_id removes all information about that product, including product_name, category, and unit_price.
Additionally, if a sales_rep_id is linked to only one order, deleting that record removes information about the sales representative such as sales_rep_name, sales_rep_email, and office_address.
This leads to unintended data loss and violates data integrity principles.
