# MAUI Grid inside Scrollview don't respect Margin and don't Center properly

MAUI app is **not respecting the Margins when using WidthRequest that is larger than screen** (iOS and Android).
When **rotating the app also doesn't Center properly** on Android (iOS works).

The layout is simplified here, but on Xamarin Forms it works even with more complex layouts with StackLayout and VisualStates that change the layout when rotating the device.

I'm focusing on Android for this issue to keep it simple, but I also checked on iOS.
On iOS the margins are also not respected but centering works after rotating the device.

## Sample Layout used:
```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiAppGridCenteredWidthBounds.MainPage">

    <ScrollView HorizontalOptions="Fill" VerticalOptions="Fill" Orientation="Vertical" BackgroundColor="Aquamarine">
        <Grid HorizontalOptions="Center" VerticalOptions="Center" BackgroundColor="Gray">
            <Grid.RowDefinitions>
                <RowDefinition Height="3*" />
                <RowDefinition Height="Auto" />
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>

            <Grid Grid.Row="1" RowDefinitions="Auto, Auto" Margin="20">

                <Grid Grid.Row="0" RowDefinitions="Auto, Auto" Margin="30" 
                      HeightRequest="125" WidthRequest="450"
                      VerticalOptions="Center" HorizontalOptions="Center"
                      BackgroundColor="Yellow" />

                <Grid Grid.Row="1" Margin="30" RowDefinitions="Auto, Auto"
                      WidthRequest="450" HeightRequest="400" 
                      HorizontalOptions="Center" VerticalOptions="Center" 
                      BackgroundColor="Green"/>
            </Grid>
        </Grid>
    </ScrollView>

</ContentPage>
```

## Screenshots / Video

Xamarin Forms             |  MAUI
:-------------------------:|:-------------------------:
![Xamarin Centered Portrait](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/c7dd73b1-bee7-492a-9b12-3826f6a648a3) | ![MAUI Centered Portrait](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/4ccc318e-cb09-4748-bdc2-9a4d5bdc7f8b)
![Xamarin Centered Landscape](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/7c166213-293c-40fb-922a-3852476ce2d4) | ![MAUI Centered Landscape](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/7240c899-170f-4065-8a34-d495329c0172)
![Xamarin Centered Grid](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/faa2b48c-93d5-4576-992a-6c52019a4fa7) | ![MAUI Centered](https://github.com/dinisvieira/maui-centered-grid-width-bounds/assets/2824952/c2338a17-312c-4411-9c1b-90503e4ac4f7)





