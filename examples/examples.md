# Examples and Inspiration

This section is intended to give new users an ideas of how Grocy can be used and existing users inspirations of how to improve or extend their existing setup.

Please contribute with your own setup!


# Simon's Setup

## Goal

To keep track of what is in the fridge and freezer to make shopping easier. To lower our food spoilage. To make sure I do not run out of standard items.

## Setup

A few words about the setup.

### Install, hardware and tools

Running the linuxserver docker container on a NUC with Ubuntu. In the kitchen we have an old Fire Tablet (gen 5?) with the a full screen browser showing the Grocy page. Connected to the tablet is a noname bluetooth barcode scanner.

While shopping Grocy shopping list is used via the web UI or products are purchased directly with the PantryParty app.

For consuming dishwasher tablets (only so far) I integrated Grocy with Home Assistant which keep track of when the dishwasher is run.

### Config

#### Settings

Localizations such as start of week. Only workflow setting changed from default is disabling of the price feature:

```
Setting('FEATURE_FLAG_STOCK_PRICE_TRACKING', false);
```
#### Workflow

All items have a rough default best before date. We have decided to not care about the exact date.

Most items have the same purchase and stock quantity unit. Only 3 states are used. Full, opened and empty. When a packaged is opened it is opened in Grocy and when the packing is thrown away it is consumed. Every glass of milk or similar is not tracked. As many brands/package sizes are connected to the same product. The idea is that you mostly buy what you usually buy anyways and I do not care about what brand of milk I happen to have in the fridge. With the idea, keep it simple and easy and details when needed

### Initial Setup/Stock Take

The initial stock take was done with a bluetooth scanner connected to a laptop. The most essential locations and product groups were added. Via the purchase screen most products were added using the function *add as new product with prefilled barcode*.