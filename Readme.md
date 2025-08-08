# Custom Navigation Bar (MagicBar)

This project is a custom navigation bar control for WPF applications, named `MagicBar`. It provides an interactive and animated navigation experience. The control is based on a `ListBox` and features a "magic" moving circle that highlights the selected item.

![MagicBar Demo](https://i.imgur.com/your-demo-image.gif) <!-- Replace with an actual GIF -->

## Features

- **Interactive Navigation**: A `ListBox`-based control that's easy to use and bind to data.
- **Smooth Animations**: The control features smooth animations for item selection, including a moving highlight circle and effects on the item's icon and text.
- **Customizable Items**: You can easily customize the text and icon for each navigation item.
- **Styled with XAML**: The control's appearance is defined in `Themes/Generic.xaml` and can be customized to fit your application's theme.

## How to Use

To use the `MagicBar` control in your WPF application, follow these steps:

1.  **Add a reference to the `CustomNavigationBar` project or DLL.**
2.  **Add the namespace to your XAML file:**

    ```xml
    xmlns:navigation="clr-namespace:CustomNavigationBar;assembly=CustomNavigationBar"
    ```

3.  **Add the `MagicBar` control to your view:**

    ```xml
    <navigation:MagicBar x:Name="bar">
        <ListBoxItem Content="Microsoft" Tag="{x:Static james:IconType.Microsoft}"/>
        <ListBoxItem Content="Apple" Tag="{x:Static james:IconType.Apple}"/>
        <ListBoxItem Content="Google" Tag="{x:Static james:IconType.Google}"/>
        <ListBoxItem Content="Facebook" Tag="{x:Static james:IconType.Facebook}"/>
        <ListBoxItem Content="Instagram" Tag="{x:Static james:IconType.Instagram}"/>
    </navigation:MagicBar>
    ```

    *Note: This example uses the `JamesIcon` library for the icons. You will need to have this library referenced in your project.*

## Customization

### Items

Each item in the `MagicBar` is a `ListBoxItem`. You can customize the text and icon for each item by setting the `Content` and `Tag` properties, respectively.

-   **`Content`**: The text to be displayed for the item.
-   **`Tag`**: The icon to be displayed for the item. The `MagicBar` is styled to work with the `JamesIcon` library, but you can modify the `ItemContainerStyle` in `Themes/Generic.xaml` to use a different icon source.

### Appearance

The appearance of the `MagicBar` is defined in `Themes/Generic.xaml`. You can modify the styles in this file to change the colors, fonts, sizes, and animations of the control.

Key styles to look at:

-   **`MagicBarItem`**: The style for the `ListBoxItem`s. You can change the `ControlTemplate` to modify how each item is rendered.
-   **`Bar`**: The style for the main background bar.
-   **`Circle`**: The style for the moving highlight circle.
-   **`Arc`**: The style for the "scooped" shape of the highlight circle.

## How It Works

The `MagicBar` control is a subclass of `ListBox`. The core logic is in `MagicBar.cs`.

When the `SelectionChanged` event is triggered, a `Storyboard` animation is started. This animation moves a `Grid` element named `Part_Circle` horizontally. The position is calculated based on the `SelectedIndex` of the `ListBox`.

The visual appearance and the animations for the items themselves (icon moving up, text appearing) are defined in the `ControlTemplate` of the `ListBoxItem` in `Themes/Generic.xaml`.

## Dependencies

-   **Jamesnet.Wpf.Controls**: This control uses the `JamesIcon` and animation classes from the `Jamesnet.Wpf.Controls` library. Make sure you have this dependency in your project.

## Project Structure

-   **`CustomNavigationBar/`**: Contains the source code for the `MagicBar` control.
    -   `MagicBar.cs`: The code-behind for the control.
    -   `Themes/Generic.xaml`: The default style and template for the control.
-   **`TestApp/`**: A sample application demonstrating the usage of the `MagicBar` control.
    -   `MainWindow.xaml`: The main window of the test application, showing how to use the `MagicBar` in XAML.
    -   `MainWindow.xaml.cs`: The code-behind for the main window.
