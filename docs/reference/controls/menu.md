---
description: REFERENCE - Built-in Controls
---

# Menu

The menu control can add menu structure to an application. You will usually place a menu at the top edge of a dock panel control, so that it is drawn at the top of a window.

{% hint style="info" %}
For reference information about the dock panel, see [here](dockpanel.md).
{% endhint %}

## Menu Items

A menu element will usually contain a set of nested `<MenuItem>` elements. The first level of menu items defines the horizontal part of the menu. Subsequent levels of menu items are drop-downs.

The caption of a menu item is set by the `Header` property. The content zone of a menu item can contain sub-items if required.

You can add menu separator lines by including a `<Separator>` element or by adding a menu item with its header set to the minus sign, like this:

```xml
<MenuItem Header="-" />
```

## Useful Properties

You will probably use these properties most often:

<table><thead><tr><th width="147.33333333333331">Element</th><th width="190">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Menu</code></td><td><code>DockPanel.Dock</code></td><td>Position the menu on the top edge of a dock panel.</td></tr><tr><td><code>MenuItem</code></td><td><code>Header</code></td><td>The menu item caption.</td></tr><tr><td><code>MenuItem</code></td><td><code>Command</code></td><td>The command to be executed when the menu item is clicked or selected with the keyboard.</td></tr><tr><td><code>MenuItem</code></td><td><code>MenuItem.Icon</code></td><td>Contains an icon graphic to display alongside the menu item.</td></tr><tr><td><code>Separator</code></td><td></td><td>A menu item separator line.</td></tr></tbody></table>

## Example

This example creates a menu docked at the top edge of a window.&#x20;

```markup
<Window ...>
    <DockPanel>
    <Menu DockPanel.Dock="Top">
      <MenuItem Header="_File">
        <MenuItem Header="_Open..."/>
        <Separator/>
        <MenuItem Header="_Exit"/>
      </MenuItem>
      <MenuItem Header="_Edit">
        <MenuItem Header="Copy"/>
        <MenuItem Header="Paste"/>
      </MenuItem>
    </Menu>
    <TextBlock/>
  </DockPanel>
</Window>
```

<!--figure><img src="../../.gitbook/assets/menu.gif" alt=""><figcaption></figcaption></figure-->

## Accelerator Keys

An accelerator key is identified by a single letter in the header preceded by an underscore. For example:

```xml
 <MenuItem Header="_File">
```

It allows the user to access a menu item quickly. It is also sometimes called a hot key, access key or mnemonic.

The user can access this feature by first pressing the Alt key, and then the accelerator key (or they can be pressed together). This is demonstrated in the second of the menu sequences in the example above.

You will see that accelerator keys, where defined, are underlined on the menu as soon as the Alt key is pressed. Then any sub-menus are dropped down as soon as the accelerator key above is pressed.&#x20;

Once keyboard interaction has been initiated with the Alt key, the user can also navigate the menus using the keyboard arrow keys. Menu items may be selected using the Enter key on the keyboard.

## Menu Commands <a href="#menu-commands" id="menu-commands"></a>

To initiate an action, the command property of a menu item can be bound to an `ICommand` object. The command will be executed when the menu item is clicked or selected with the keyboard. For example:

```markup
<Menu>
    <MenuItem Header="_File">
        <MenuItem Header="_Open..." Command="{Binding OpenCommand}"/>
    </MenuItem>
</Menu>
```

{% hint style="info" %}
For guidance on how to bind to commands, see [here](broken-reference).
{% endhint %}

## Menu Icons <a href="#menu-icons" id="menu-icons"></a>

A menu icon can be displayed by placing an image or a path icon in the `<MenuItem.Icon>` attached property. For example:

```markup
<<MenuItem Header="_Edit">
  <MenuItem Header="Copy">
     <MenuItem.Icon>
        <PathIcon Data="{StaticResource copy_regular}"/>
     </MenuItem.Icon>
  </MenuItem>
  <MenuItem Header="Paste">
     <MenuItem.Icon>
        <PathIcon Data="{StaticResource clipboard_paste_regular}"/>
     </MenuItem.Icon>
</MenuItem>
```

<!--figure><img src="../../.gitbook/assets/menu2.gif" alt=""><figcaption></figcaption></figure-->

{% hint style="info" %}
For more detailed guidance on how to add icons to your menus, see [here](../../guides/graphics-and-animation/how-to-add-menu-icons.md).
{% endhint %}

## More Information <a href="#dynamically-creating-menus" id="dynamically-creating-menus"></a>

{% hint style="info" %}
For the complete API documentation about this control, see [here](http://reference.avaloniaui.net/api/Avalonia.Controls/Menu/).
{% endhint %}

{% hint style="info" %}
View the source code on _GitHub_ [`Menu.cs`](https://github.com/AvaloniaUI/Avalonia/blob/master/src/Avalonia.Controls/Menu.cs)
{% endhint %}