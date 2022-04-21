After 0.7 update the new merchants were added, where you can buy and sell weapons, vehicles and a lot of other things.
So if you have items you don't need, you can sell them and buy things you really need with the money you get.
Unfortunately, we were not told much about the settings and the newly introduced EconomyOverride.json file, which defines how the trader works and what things can be sold and bought.

I have taken a few days to test everything extensively and summarized the whole thing for you, as well as created a file for you that contains all the items that are currently available.

The items are sorted alphabetically so it is relatively easy to find something, you just have to copy the settings of the A0 dealers and paste them into the desired dealers.
The file will be updated regularly.

Now we start directly with the settings and possibilities of the trader.

You can find the file for the singleplayer by navigating to the path below.

`C:\Users\<username>\AppData\Local\SCUM\Saved\Config\WindowsNoEditor\EconomyOverride.json`

For servers you should find a corresponding file in Configuration Files settings of the server.
These files are compatible with each other, which means that in singleplayer you can set everything as you wish and then simply transfer the file or its contents to the server.

Let's start with the basic settings and their meaning

# Basic settings

`"enable-economy": "1",`
This command determines if the merchant is Enabled or Disabled, where 1 = Enabled and 0 = Disabled. By default this is set to 1.


`"economy-reset-time-hours": "-1.0",`
This sets how long it takes for traders to regenerate their money, as well as how long it takes for items to become available again (replenished).
-1 is the default value, here it takes about an hour until something is replenished.
At 0 or less (except -1) nothing will be replenished. Important is that a value like 0.1 does not work, but the whole thing starts from 1, so one hour is the minimum that can be used.


`"prices-randomization-time-hours": "-1.0",`
This value defines how long it takes for prices to change randomly, again -1 is the default value, which means that the price changes after one hour, if this value is set to 0, the prices stay constant. 1.0 = 1 hour, 2.0 = hours etc.



`"fully-restock-tradeable-hours": "2.0",`
This sets how long it will take for items to be sold again after they are no longer available, 2.0 is the default value, which means that a sold out item will be available again after 2 hours. If this value is set to 0, no items will be replenished.


`"trader-funds-change-rate-per-hour-multiplier": "1.0",`
This means how long it takes traders to replenish their money per hour. Default value is 1, which means that the normal rate is added, at 2.0 it is doubled, at 3.0 it is tripled and so on.


`"traders-unlimited-funds": "0",`
As it says there, this value determines if traders will lose money when you sell them items, 0 = money will be less, 1 = money is unlimited, so the traders will not lose money when you sell them items.

### These are the most important settings, you should play around with them in singleplayer to see what happens, because you can easily ruin your economy.


# Vehicle settings

In the next part we will talk about the `"limited-vehicles": `
This is about the maximum number of vehicles a dealer can sell, most of it is self-explanatory, but I'll go into it a bit anyway.

  `"limited-vehicles": [


        {


          "vehicle-group": "VehicleSpawnGroup.PickupTruck",

Here we define which vehicle group we are dealing with

          "vehicle-group-max-amount": "14"

This is the maximum number that will be sold before no more vehicles of this type can be bought.
This applies to all vehicle groups and should be understandable so far.


# Remove items / change prices


It is a bit more difficult with the items that the dealers buy and sell.
Basically you can change all values and also remove items from the inventory completely if you want.
However, it is currently not possible to let a merchant sell items that he does not offer by default.
For example, I can't let the "General Goods" trader sell MK18, but I can delete the MK18 from the "Armory" trader's inventory and thus prevent the purchase.
Now I will explain the entries and their values in general before I explain how to change or remove items.


          `"tradeable-code": "BP_Weapon_M82A1",
          "base-purchase-price": "-1",
          "base-sell-price":"-1",
          "delta-price":"-1.0",
          "can-be-purchased": "default"`

   * "tradeable-code": "BP_Weapon_M82A1", = indicates which item it is.
   * "base-purchase-price": "-1", = This is the purchase price of the item, it indicates how much the item costs at the dealer.
   * "base-sell-price": "-1", = This is the price for which the item can be sold at the respective merchant.
   * "delta-price": "-1.0", = The delta price is a price multiplier, the given price is multiplied with it.
   * "can-be-purchased": "default" = indicates whether the item can be purchased.


As an example we will now change the item and adjust the price.
First we change the item type to a M16, for this we simply change the [tt]tradable-code[/tt] to the respective spawncode of the desired item, in our case to a M16

`"tradeable-code": "BP_Weapon_M16A4",`


If we are not satisfied with the price at the dealer, we can simply change it, "-1" is the default value, that is the price the item normally costs, but since we are not satisfied with it we change it to 25,000, this then looks like this.
`"base-purchase-price": "25000",`


Now of course we are not satisfied with how much we can sell the item for, so we change the price to 12500, this will look like this
`"base-sell-price": "12500",`


Now we have successfully changed the item and adjusted the prices, but we are still not satisfied with it, but we don't want to change all the values again, now we set the [tt]delta-price[/tt] simply to double the price
`"delta-price": "2",`
3 = would triple the value, 4 = quadruple and so on.
At 0 or less, the value does not change.
In this case the M16 would now cost 50000 to buy and 25000 to sell because both prices are multiplied by the [tt] delta-price[/tt].


But now we are not satisfied with this and don't want the item to be sold at all, so we change [tt]can-be-purchased[/tt] to
`"can-be-purchased": "false"`

Now the item disappears completely from the merchant

   * true = the item will be sold (doesn't work to add items that the merchant doesn't sell anyway)
   * false = the item will be removed from the list and can't be bought anymore (the sale still works)
   * default = The item will be displayed as it is by default, the prices can still be changed if desired.


That's about it, I hope this guide helped you and will help you to set up your merchant the way you want.
If you have any further questions, please feel free to contact me






