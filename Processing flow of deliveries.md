# Processing Flow of Deliveries
You can keep track of your company deliveries by creating deliveries documents in the Deliveries (DC304000) form and planning these deliveries using the Delivery Planning (DC501000) form.
For faster data entry, you can specify a delivery class in the Delivery Classes (DC203000) form, that will be used when creating documents in Deliveries (DC304000) entry form.

> __Note__ You cannot delete a delivery class if it is already associated with a delivery. If the delivery is confirmed but does not yet have the *Shipped* status, you can click **Correct** in the form toolbar, dissociate the delivery class from the delivery and confirm the delivery. Then you can delete the delivery class.

#### In This Topic

* [Prerequisites](#prerequisites)
* [Creating a Delivery](#creating-a-delivery)
* [Creating sales orders and shipments documents](#creating-sales-orders-and-shipments-documents)
* [Creating a Delivery planning](#creating-a-delivery-planning)
* [Disassociation of documents from deliveries](#disassociation-of-documents-from-deliveries)
  * [Delivery doc. type in the Domestic Carriers preferences form is set to Sales Orders](#delivery-doc-type-in-the-domestic-carriers-preferences-form-is-set-to-sales-orders)
  * [Delivery doc. type in the Domestic Carriers preferences form is set to Shipments](#delivery-doc-type-in-the-domestic-carriers-preferences-form-is-set-to-shipments)
* [Related Articles](#related-articles)

## Prerequisites
Before you start creating a delivery and a delivery plan, make sure the following settings are configured in the system and the necessary documents are created.

| Form | Action | Notes |
| --- | --- | --- |
| Shipping Zones (CS207510) | Define the shipping zones which you will associate later with deliveries, sales orders and shipments. |  |
| Domestic Carriers Preferences (DC101000) | Configure all the settings in the **Delivery Settings** section of the form. | If there are already planned deliveries in the system, we do not recommend to change the **Delivery Doc. Type** setting. The system does not support the use of mixed functionality, with part of planned deliveries on sales orders and part on shipments.<br>The documents table of the delivery planning form displays both sales orders and shipments if  **Delivery doc. type** is set to *Sales Order*, and  only shipments if **Delivery doc. type** is set to *Shipments*. |
| Order Types (SO201000) | In the **General Settings** tab, **Order Settings** section, you must select the **Supports Delivery Planning** check box for all order types for which you want to use the delivery planning functionality. By default, the **Sales Order** type has this check box already selected. | |

## Creating a Delivery
1. Open the Deliveries (DC304000) form.
2. (Optional) in the **Delivery Class ID** box, select an existing delivery class.
3. In the **Description** box, type a description for the delivery.
4. In the **Branch** box, select a branch.
5. In the **Loading Date** box, select the date when the items are loaded in the vehicle.
6. In the **General Settings** tab, add shipping zones in the **Shipping Zone** section. You can use either **Add Row** ![Add Row](/images/add button.JPG) (to add zones one by one) or the **Add Shipping zones** button in the table toolbar (to add zones in bulk). 

   > **Note** In the delivery planning, only sales orders, shipments and deliveries that share the same shipping zones are displayed.
 
7. In the **Vehicle Info** section fill in the necessary details.

   > **Note** The elements of the **Attributes** tab of this form cannot be edited. To associate attributes to the delivery:
   > - define them in the Attributes (CS205000) form.
   > - associate the created attributes with an existing delivery class by adding it in the **Attributes** tab of the delivery class.
   > - select the delivery class in the delivery form.
   > The elements of the **Documents** tab cannot be edited. This tab displays the documents that are associated with the delivery in the Delivery Planning (
DC501000) form.

8. Deselect the **Hold** check box in the header of the form. 

   > **Warning** If the status of the delivery is *Open* and it has associated documents in the Delivery Planning (DC501000) form, the **Hold** check box is disabled. You must first disassociate the documents. For details, see [Disassociation of documents from deliveries](#disassociation-of-documents-from-deliveries) below.

9. Click **Save** ![Save](/images/save button.JPG) in the toolbar of the form.

   > **Warning** A delivery cannot be deleted if it is used in a delivery planning and has documents associated. You must first disassociate the documents. For details, see [Disassociation of documents from deliveries](#disassociation-of-documents-from-deliveries) below.

## Creating sales orders and shipments documents
Create the necessary sales orders or shipments which you want to further use in delivery plannings.
For them do be displayed in the delivery planning form, they must fulfill the following requirements:
* if **Delivery doc. type** in the Domestic Carriers preferences form is set to *Sales Order*:
  * all order types to be used in a delivery planning, must have the **Supports Delivery Planning** checkbox selected in Order Types (SO201000), **General Settings** tab, **Order Settings** section. By default, the *Sales Order* type has this check box already selected.
  * sales orders and deliveries must share the same shipping zones.
  * the sales order's status must be *Open*, *Backorder*, *Shipped* or *Shipping*.
  * the value in the **Open Qty.** column of the **General Settings** tab of the sales order must be greater than 0.
* if **Delivery doc. type** in the Domestic Carriers preferences form is set to *Shipments*:
  * shipments and deliveries must share the same shipping zones.
  * the shipments' status must be *Open* or *Confirmed*.

## Creating a Delivery planning
   > **Note** If you keep the delivery planning form open while you make changes in the system that should affect the delivery planning, you must refresh the deliveryplanning page to see them.

1. Open the Delivery Planning (DC501000) form.
2. In the **Start Date** box select the start date of the period based on which deliveries are displayed in the form.
3. In the **End Date** box select the end date of the period based on which deliveries are displayed in the form.
4. In the **Delivery Doc. Offset Days** box type the number of days prior and after the loading date of goods (specified in the delivery) depending on which the sales orders and shipments are displayed in the documents table of this form.

   > **Note** The **Sched. Shipment** date of sales orders (in the **Shipping Settings** tab of the sales order form) and the **Shipment Date** of the shipment (in the header of the shipment form) must be within the interval given by the loading date of the delivery (in the header of the delivery form) and the offset days set in the header delivery planning form.

5. Below, there are three tables:
- the one on the left represents the deliveries table
- the one on the right represents the documents table
- the bottom table is one where custom information can be added

Depending on the setting of the **Delivery doc. type** field in the Domestic Carriers Preferences (DC101000) form there are two different types of documents that will be displayed in the **Documents** table:

   5. if the value is set to *Sales Order*, sales orders will be displayed in the **Documents** table. To associate a delivery with a document select the delivery and the sales order and click **Allocate** in the delivery table toolbar.

If the order has a shipment, that shipment will appear in the table if the *All Records* value is selected in the filter. Only the sales order can be associated with the delivery. When the shipment is confirmed, the delivery will also be associated with it.

> **Note** If the order has been shipped in full, until the delivery is confirmed, the Sales Order will not be visible in the grid, only the shipment. After the confirmation, both documents will appear.

After all the documents have been allocated to the delivery, the delivery can be confirmed using the **Confirm** button in the table toolbar. Now you can click **Ship** in the delivery table toolbar.

  > **Warning** An order can be associated with multiple deliveries only if it supports Back Order, and the previous delivery has been confirmed.

   5. if the value is set to *Shipments*, shipments will be displayed in the **Documents** table. To associate a delivery with a document select the delivery and the shipment and click **Allocate** in the delivery table toolbar. After the shipment has been confirmed, the delivery can also be confirmed and it’s status set to *Shipped* by clicking **Confirm** and then **Ship** in the table toolbar.

  > **Warning** A shipment cannot be planned on multiple deliveries.
  > To change a delivery status to *Shipped*, the sales order associated must have a shipment associated and confirmed.

6. Optional: the deliveries that were associated with documents are also displayed in the following locations:
* Sales Orders (SO301000) > Shipping Settings tab
* Shipments (SO302000) > Shipping Settings tab > Shipping Information section > Associated Delivery field
* Process Orders (SO501000)
* Process Shipments (SO503000)

  > **Note** In case you need to correct a shipment which is associated with a delivery planning, you must first click **Correct** in the associated delivery, and then open the shipment and click **Actions** > **Correct Shipment** in the form toolbar.

7. The custom table, in the lower part of the delivery planning form, can be configured to display custom fields. For more information regarding the way custom fieldscan be added, see [Adding Custom Information to Delivery Planning](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)

## Disassociation of documents from deliveries

Below you will find methods of disassociating documents from deliveries, depending on the option selected in the **Delivery doc. type** field, in the Domestic Carriers Preferences form.

### Delivery doc. type in the Domestic Carriers preferences form is set to Sales Orders

> **Note** The **Allocate** button in the **Deliveries** table toolbar can also be used when a document needs to be deallocated from the delivery. The document must be deselected and the **Allocate** button clicked.

* If you have a sales order associated with a delivery, with status *Confirmed* or *Shipped*:
  1. Select the delivery.
  2. Click **Correct** in the deliveries table toolbar.
  3. Deselect the sales order, in the documents table.
  4. Click **Save** in the form toolbar.

* If you have a sales order with confirmed shipment, associated with a delivery, with status *Confirmed* or *Shipped*:
  1. Select the delivery.
  2. Click **Correct** in the deliveries table toolbar.
  3. Open the shipment, by clicking on its ID link.
  4. On the shipment form, click **Actions** > **Correct Shipment** in the form toolbar.
  5. Return to the delivery planning form, select the delivery and click **Correct** in the deliveries table toolbar. Observe that the shipment was automatically disassociated.
  6. (Optional) If you want to further disassociate the sales order, open the shipment again and delete it. Then return to the delivery planning form, select the delivery and deselect the associated order. Alternatively, you can open the sales order, go to **Shipping Settings** tab, select the desired delivery in the table of deliveries and click **Delete Row** ![Delete Row](/images/delete button.JPG).
  7. After you finish disassociating documents, click **Save** in the form toolbar.

> **Note** If an order associated with a delivery was cancelled in the meantime, it will still be displayed in the documents table and it can be disassociated by clicking **Correct**, as long as it is not associated with a shipment.

### Delivery doc. type in the Domestic Carriers preferences form is set to Shipments
1. Select the delivery.
2. Click **Correct** in the deliveries table toolbar.
3. Deselect the shipment, in the documents table.
4. Click **Save** in the form toolbar.

## Related Articles
* [Adding Custom Information to Delivery Planning](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Domestic Carriers Preferences (DC101000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Deliveries (DC304000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Delivery Classes (DC203000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Delivery Planning (DC501000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Shipping Zones (CS207510)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Order Types (SO201000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
* [Attributes (CS205000)](https://bflorentina.github.io/Rewrite/Processing%20flow%20of%deliveries)
