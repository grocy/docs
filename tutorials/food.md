# Use: track your food!

## Table of content

* [Table of content](#table-of-content)
* [Goal](#goal)
* [Before you start](#before-you-start)
* [Stock overview](#stock-overview)
* [Manage master data](#manage-master-data)
  + [Products](#products)
    - [Add and Edit Products](#add-and-edit-products)
    - [Parent Products](#parent-products)
  + [Locations](#locations)
    - [Freezers](#freezers)
  + [Stores](#stores)
  + [Quantity Units](#quantity-units)
  + [Product groups](#product-groups)
* [Purchase](#purchase)
  + [Creating a product when purchasing](#creating-a-product-when-purchasing)
  + [Scan mode](#scan-mode)
* [Consume](#consume)
  + [Scan mode](#scan-mode-1)
* [Shopping list](#shopping-list)
* [Transfer](#transfer)
* [Inventory](#inventory)

## Goal
Grocy lets you keep track of all your food. See what you have at home, what is about to expire, what is below minimum stock and needs to be bought, manage shopping lists.

## Before you start
You will need:
- a working Grocy app or installation
- food you want to keep track of

Helpful but not required:
- barcode scanner

## Stock overview

When you login to your Grocy instance, or open the demo, you will see the stock overview. This is the main window you normally work from if you use Grocy for food. Here you can filter products based on name, stock level or if a product is getting old.

![Stock Overview](/images/stockoverview.png)

## Manage master data
When you start a fresh Grocy installation you have to start by setting up your database. This is done from the `manage master data` menu.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/masterdatamenu.png" width="25%"></img>


### Products

On a fresh install, before you can set up products you need to define:
- Locations
- Quantity Units
- Product Groups (optional)
- Stores (optional)

When you have defined locations and quantity units you can start adding products. One way to add products is from the `product` option in the `manage master data` section. They can also be added directly from the **purchase** screen.

#### Add and Edit Products

To add a product click **add**.

![Edit Product](/images/editproduct1.png)

Most fields are optional. The required fields have a red border.

- **Name:** Name of the product (Required)
- **Parent product:** Assign a parent product, either by entering the name or scanning barcode or scan the barcode with your camera.
- **Description:** A description of the product.
- **Barcode(s):** One or many barcodes for the product. If you want to assign the same product of different brands, you could add the barcodes of the different brands here and Grocy will consider them as the same product. Add the barcodes by scanning barcode or scan the barcode with your camera by pressing the blue button. (Note: A handheld barcode scanner enters its data the same way as a keyboard, you have to select the field before scanning.)
- **Default Location:** Default location for the product (Required).
- **QU Conversions:** Quantity unit conversions. Used by recipes. Specific for this product. E.g. 1dl flour =60g.

![Edit Product 2](/images/editproduct2.png)

- **Minimum stock amount:** If you want Grocy to warn you when you are below a defined level.
- **Accumulate sub products min. stock amount:** If the product is a parent product it will use the sum of its children(sub) products when checking if the stock is below the *Minimum stock amount*. See example below.
- **Default best before days:** If you want Grocy to pre-fill a suggestion of best before date when purchasing this product (useful for quick entry when purchasing). `-1` Means that the product never expires.
- **Default best before days after opened:** How many days the product be eatable after it is opened.
- **Product group:** What group of products the product belongs to.
- **Quantity unit purchase:** What kind of unit do you buy the product in.
- **Quantity unit stock:** What unit do you want to keep track of in stock.
- **Factor purchase to stock quantity:** The translation factor between package size you buy and that you use. If the product is 6-pack of eggs and you want to keep track of every egg, the *Quantity unit purchase* would be *pack* and the *Quantity unit stock* would be *Piece* and the *Factor purchase to stock quantity unit* would be 6. You purchase 1 pack and end up with 6 pieces in stock.
- **Allow partial units in stock:** If you want to be able to track partial units in stock. E.g. you consume half a head of lettuce and want to keep track of that, you have to enable this.

![Edit Product 3](/images/editproduct3.png)
- **Enable tare weight handling:** 
- **Tare weight:** 
- **Disable stock fulfillment checking for this ingredient:** If you do not want the check stock for this product when Grocy checks if you have enough in stock to cook a recipe. Can be overridden in the recipe.
- **Energy (kcal):** Energy content of a stock unit.
- **Default best before days after freezing:** If you move a product from the fridge to the freezer it will get a new best before date if this value is set. Note: `-1`does not work for this field and product that is put directly into the fridge will not get this value. This only applies when a product is moved to the fridge.
- **Default best before days after thawing:** Best before date when moving a product from the freezer to another location.
- **Product picture:** You can add picture to your product.

#### Parent Products

There are two kinds of products. **Products** and **Parent Products**. A parent product is a normal product that has other products connected to it. In this example *Chocolate* has both *Milk Chocolate* and *Dark Chocolate* connected to it. This can be used to make sure you never run out of chocolate, if you are only concerned that you have some kind of chocolate at home, but not what kind, but you want to keep track of if it is dark or milk. It might matter for a recipe.

![Parent product example](/images/parentproductexample.png)

Another way to use parent products can be for different package sizes.
Example, you want to have eggs at home, but sometimes you buy eggs in a pack of 6 and sometimes in a pack of 12. Then you could have Egg as a parent product and 2 child products, *Egg - pack of 6* and *Egg - pack of 12*. In a recipe you could then add the parent product.


### Locations

Locations are physical locations in your home or kitchen. Locations can be as large or small as you wish depending on how much control you wish to have.

To add a location click *Add* and give the location a name and click save.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/locations.png" width="50%"></img>

#### Freezers

Freezers are a special locations. If you check the freezer check box, items moved to the freezer will be considered **frozen** and when removed from the freezer they will be considered **thawed**. This can effect the expiry date.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/editlocation.png" width="60%"></img>


### Stores

If you have prices enabled you can use stores to keep track of the price history of different stores.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/stores.png" width="50%"></img>

### Quantity Units

Under quantity units you define what quantities Grocy should know of and how to convert between them. All kind of ways you will buy your food and keep track of usage of your food should be added here.

In the example there are pack, bottle, can, piece, milliliter, etc. 

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/quantityunits.png" width="50%"></img>


You need to give the quantity unit a name, if you wish and it is applicable you can add a unit conversion. 

**Example:**
A suitable conversion could be that 1 kg = 1000 g. This is true for all products. It would be unsuitable to add that 1 pack = 10 pieces since this is product dependent and can later be added to the products.

![Edit Quantity Units](/images/editquantityunits.png)

### Product groups

Product groups is a way to sort and arrange your inventory. This is not strictly needed for use of Grocy but can be useful for browsing your virtual kitchen.

![Product Groups](/images/productgroups.png)



## Purchase

After you purchase products at the store you can get them into the Grocy stock by using the purchase feature.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/purchase.png" width="50%"></img>


- **Product:** Select a product by typing its name or scanning its barcode. If you scan an unknown barcode or enter an unknown product name you will get the option to create a new product or add the barcode to an existing product.
- **Best Before:** Best before date of the product.
- **Never Expires:** Check this box if the product never expires.
- **Amount:** How many you are adding.
- **Price:** The price you paid for the purchase quantity unit.
    - **Unit Price/Total Price:** If the price entered is the total amount or a single item.
- **Store:** Where you bought the product.
- **Location:** Where in the kitchen you want to store the product.

### Input shorthands for date fields
For (productivity) reasons all date (and time) input (and display) fields use the ISO-8601 format regardless of localization.
The following shorthands are available:
- `MMDD` gets expanded to the given day on the current year, if > today, or to the given day next year, if < today, in proper notation
  - Example: `0517` will be converted to `2018-05-17`
- `YYYYMMDD` gets expanded to the proper ISO-8601 notation
  - Example: `20190417` will be converted to `2019-04-17`
- `YYYYMMe` or `YYYYMM+` gets expanded to the end of the given month in the given year in proper notation
  - Example: `201807e` will be converted to `2018-07-31`
- `x` gets expanded to `2999-12-31` (which I use for products which never expire)
- Down/up arrow keys will increase/decrease the date by 1 day
- Right/left arrow keys will increase/decrease the date by 1 week
- Shift + down/up arrow keys will increase/decrease the date by 1 month
- Shift + right/left arrow keys will increase/decrease the date by 1 year

### Creating a product when purchasing

If you enter a name or scan an unknown barcode you will get this dialog.

![Purchase unknown products](/images/purchaseunknown.png)


If you entered a name select `Add as new product`, you will be taken to the add product page with the name pre-filled (See [above](#add-and-edit-products) for more details).

If you scanned a new item that you have never bought before select `Add as new product and prefill barcode`, you will be taken to the add product page with the barcode pre-filled (See [above](#add-and-edit-products) for more details)

If you scanned an item that you have in stock, but with another brand, and you want to connect it to an exiting product, select `Add as barcode to existing product`. You will be directed back to the purchase page with that small change (see below). That barcode you scanned is now written in **bold** below the product field and the product you select will get that barcode added to its list of barcodes. 

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/purchaseaddbarcodetoexisting.png" width="50%"></img>

### Scan mode

On top of the screen you can select **Scan mode off** or **Scan mode on**. The intention is to make it fast to purchase item with a scanner. For scan mode to work as intended:
- best before date must be filled with a default value or disabled in the config.

**Note:** Price will not be entered (if it is enabled)

When you purchase with scan mode it will purchase one of the purchase unit.

## Consume

Consume is the operation used when you want to **remove** or **open** stock units.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/consume.png" width="50%"></img>

- **Product:** Select a product by typing its name or scanning its barcode.
- **Amount:** Select how many of the product you want to consume
- **Location:** Select from which location in the kitchen the product shall be consumed.
- **Use a specific stock item:** If you want to consume something else than the oldest individual of this product.
- **Spoiled:** If you want to mark the item as spoiled, to be able to keep track of how much you spoil.
- **Recipe:** If you are cooking a recipe and want to keep track.
- **OK:** Consumes what you have entered.
- **Mark as opened:** Mark the product as opened instead of consumed. Used to change expiry date and depending on setting might not count towards minimum stock.

### Scan mode

On top of the screen you can select **Scan mode off** or **Scan mode on**. The intention is to make it fast to consume item with a scanner. 

When you purchase with scan mode it will consume one of the stock quantity unit.

## Shopping list

Shopping list, is what it sounds like, a Grocy connected shopping list. When starting a new instal you automatically have one shopping list called shopping list but you can create more if you wish.

- **Add item:** Adds items to the shopping list by name or barcode.
- **Clear list:** Clears the shopping list.
- **Add products that are below defined min stock:** Add all items that you are missing to the shopping list.
- **Add all list items to stock:** Takes you too the purchase window with the items in the shopping list pre-filled.


<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/shoppinglist.png" width="70%"></img>

- **[Green] Mark as done:** Strikes through the item on the shopping list. Does nothing more than to help you keep track.
- **[Cyan] Edit this item:** Change the shopping list item. Product or amount.
- **[Red] Delete this item:** Removes the item from the shopping list.
- **[Blue] Add to stock:** Opens the purchase window with the items from the shopping list pre-filled.

- **Notes:** A free form field for notes.
 

## Transfer

The transfer feature is a way to move items around in your virtual kitchen.

If you move an item to the freezer it will be considered **frozen** and if you move it out it will be considered **thawed**. If you have it setup on the product page this will effect the expiry date.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/transfer.png" width="35%"></img>

## Inventory

Inventory is a way to do a stock take. It adds or remove units in the stock quantity unit.

When trying to inventory unknown barcodes or items it behaves the same way as when [purchasing unknown items](#creating-a-product-when-purchasing). After you have created the new product you will be returned to the inventory window to continue your stock take.

<img src="https://github.com/grocy/docs/blob/4da24a279402d8ef01151d3e7f32c8712d0eb0d1/images/inventory.png" width="35%"></img>
