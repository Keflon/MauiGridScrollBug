# iOS bug. 

## Auto-sized Grid row containing ScrollView sizes itself to the full height requested by the ScrollView content.
MAUI bug [#15085](https://github.com/dotnet/maui/issues/15085)

Given the following xaml:
```xaml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiGridScrollBug.MainPage">

    <Grid RowDefinitions="*,*">
        <ScrollView Grid.Row="0">
            <Button HeightRequest="600" Text="Top Button" Margin="5"/>
        </ScrollView>
        <ScrollView Grid.Row="1">
            <Button HeightRequest="600" Text="Bottom Button" Margin="5"/>
        </ScrollView>
    </Grid>
</ContentPage>
```
### Expected result is a ContentPage with 2 equally sized Grid rows.  
![image](https://github.com/dotnet/maui/assets/16598898/c83da0bc-caa9-45a7-a0c3-1a96a7f29233)

### Actual result
On iOS, the grid rows expand to the size of their ScrollView Content.
![image](https://github.com/dotnet/maui/assets/16598898/1bb49c47-e295-47ad-bcc4-8d961eb8f493)

