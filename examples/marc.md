
# Marcs's Setup

## Goal

Automatically generating shopping lists, tracking food in fridge and freeze, tracking chores (eg. watering plants).

## Setup

I am using Grocy in combination with a wireless barcode scanner and [Barcode Buddy](https://github.com/Forceu/barcodebuddy) (disclaimer: I am the developer of Barcode Buddy, which is why I make extensive use of it in my setup).

### Install, hardware and tools

I am running both Grocy and Barcode Buddy on a bare metal server (J5005, which is a low power, always-on server) with a headless Ubuntu installation. The barcode scanner is a generic $30 China model that registers as a USB keyboard and has a range of about 20m. The keyboard input is grabbed by Barcode Buddy with [this script](https://github.com/Forceu/barcodebuddy/blob/master/example/grabInput.sh).

In my kitchen I also have a laminated list sheet of paper with barcodes for products that normally do not have a barcode (eg. loose vegetables), in addition to special Barcode Buddy barcodes.

With Barcode Buddy most of the tasks are automatic, therefore I do not need a display or tablet in my kitchen. As I have a laser barcode scanner, very reflective / shiny surfaces as plastic can be sometimes a problem. In that case I use the Barcode Buddy Android app.

### Config

#### Settings

Localizations such as currency. Also I disabled the following features, as I do not use them:

```
Setting('FEATURE_FLAG_TASKS', false);
Setting('FEATURE_FLAG_BATTERIES', false);
Setting('FEATURE_FLAG_EQUIPMENT', false);
```

#### Workflow


##### Groceries

All items have a rough default best before date, which is surprisingly quite accurate. I am using generic products, instead of a single product for each brand / size: for example three different chocolate bars would all be tracked as the product "Chocolate". For larger items (eg. cartons of milk) I track the quantity, for smaller items I do not and scan them out once all items are consumed (eg. dishwasher tabs).

###### Purchasing

I am using the Shopping List feature to track what products are below minimum stock and manually add items that I will need for the meals that I planned for the week. Once I bought them and arrive at home, I scan a special barcode to put Barcode Buddy into Purchase Mode. Then I scan all products that I bought - if the product's barcode has been associated with a Grocy product before, it will automatically be added to Grocy's stock and removed from the shoppinglist. If not, it will be looked up and I can add it from the Web UI afterwards. During this process I open Barcode Buddy's Screen Module on my phone to have an indication if there are any products that could not be looked up. 


###### Consuming

When I am throwing something away or if a product is nearly empty and I am about to go shopping, I will simply scan the barcode with my barcode scanner. No further action is required, as Barcode Buddy automatically removes it from Grocy's stock.

If I opened a product without completely consuming it, I put Barcode Buddy into "Open" mode and scan the item to keep track of items that are opened and might spoil faster.

##### Chores

I have chores for watering my plants, changing linen, cleaning and other various, periodic events. For some of them I have a barcode printed out, which I can scan with my barcode scanner. Barcode Buddy automatically recognises it as a chore and marks the associated one as executed. I only use barcodes for frequent chores.

### Initial Setup/Stock Take

The initial stock take was done completely manual, which took about 2 hours. If I had to do it again, it would be a lot quicker, as apps as [PantryParty](https://github.com/PantryParty/pantry_party) or Barcode Buddy make the process a lot faster.
