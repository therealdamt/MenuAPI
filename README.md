# MenuAPI
A fork of [NV6's Menu API](https://github.com/NoSequel/MenuAPI)

### Features

* Buttons that are easily controlled
* Updating menus without existing
* Paginated Menus
* Different Menu Types
* Optimized Code

### How to use

```java
@Override
public void onEnable() {
    new MenuHandler(this);
}
```

```java
@Override
public void onCommand(CommandSender sender, Command command, String label, String[] args) {
       if (!(sender instanceof Player) {
            sender.sendMessage(ChatColor.RED  + "You must be a player to run this command!"
            return;
        }
        
        Player player = (Player) sender;
        new Menu(player).updateMenu();
}
```

### Example

```java
public class ExampleMenu extends PaginatedMenu {

    public ExampleMenu(Player player, String title, int size) {
        super(player, title, size);
    }

    @Override
    public Map<Integer, Button> getButtons() {
        final Map<Integer, Button> buttonMap = new HashMap<>();

        int i = 0;

        for (AuctionItem auctionItem : AuctionPlugin.getInstance().getAuctionHandler().getAuctionItems()) {
            buttonMap.put(i, new Button(auctionItem.getStack())
                    .setClickAction(action -> {
                        auctionItem.remove();
                        getPlayer().sendMessage(CC.translate("&7Removed a crazy auction item!"));
                    }));
        }

        return buttonMap;
    }

}
```

As you guys can see, I don't need to get the ``AuctionItem`` by stack or anything, the event will already be bound to it, and it would completely work as needed 🙂

### Credits

This is a menu api of which was forked from the menu api created by [NV6](https://github.com/NoSequel). This version of the API adds a lot of features, including updating the menu without existing the player out of it [i.e the contents of the menu will change without actaully the player leaving or closing the gui at all], closing event. As well as more features.

Original Creator - [NV6](https://github.com/NoSequel)

### Contacts

* [Telegram](https://t.me/therealdamt]
* [Website](https://damt.xyz)
* Discrord - damt#0886

