# How to bind selected items in WPF TreeView

This repository describes how to bind selected items in WPF TreeView (SfTreeView).

TreeView support to select multiple items through binding the [SelectedItems](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_SelectedItems) property from view model with `ObservableCollection<object>` type.

#### XAML

``` xml
<syncfusion:SfTreeView 
            x:Name="sfTreeView"
            SelectionMode="Multiple"
            SelectedItems="{Binding SelectedNodes}"   
            ChildPropertyName="Models"
            ItemsSource="{Binding Items}" >
</syncfusion:SfTreeView>
```

#### C#

``` csharp
sfTreeView.SelectionMode = SelectionMode.Multiple;
sfTreeView.SetBinding(SfTreeView.SelectedItemsProperty, new Binding("SelectedNodes"));
```

``` csharp
public class ViewModel : NotificationObject
{
    public ObservableCollection<Model> Items { get; set; }

    public ObservableCollection<object> SelectedNodes { get; set; }
    public ViewModel()
    {
        Items = new ObservableCollection<Model>();
        SelectedNodes = new ObservableCollection<object>();
                 
        var country1 = new Model { State = "Australia" };
        var country2 = new Model { State = "Brazil" };
        var country3 = new Model { State = "China" };
        var country4 = new Model { State = "France" };            

        var aus_state1 = new Model { State = "New South Wales" };
        var aus_state2 = new Model { State = "Victoria" };
        var aus_state3 = new Model { State = "South Autralia" };
        var aus_state4 = new Model { State = "Western Australia" };

        var brazil_state1 = new Model { State = "Parana" };
        var brazil_state2 = new Model { State = "Ceara" };
        var brazil_state3 = new Model { State = "Acre" };

        var china_state1 = new Model { State = "Guangzhou" };
        var china_state2 = new Model { State = "Shanghai" };
        var china_state3 = new Model { State = "Beijing" };
        var china_state4 = new Model { State = "Shantou" };

        var france_state1 = new Model { State = "Pays de la Loire" };
        var france_state2 = new Model { State = "Aquitaine" };
        var france_state3 = new Model { State = "Brittany" };
        var france_state4 = new Model { State = "Lorraine" };
      
        country1.Models.Add(aus_state1);
        country1.Models.Add(aus_state2);
        country1.Models.Add(aus_state3);
        country1.Models.Add(aus_state4);

        country2.Models.Add(brazil_state1);
        country2.Models.Add(brazil_state2);
        country2.Models.Add(brazil_state3);

        country3.Models.Add(china_state1);
        country3.Models.Add(china_state2);
        country3.Models.Add(china_state3);
        country3.Models.Add(china_state4);

        country4.Models.Add(france_state1);
        country4.Models.Add(france_state2);
        country4.Models.Add(france_state3);
        country4.Models.Add(france_state4);

        Items.Add(country1);
        Items.Add(country2);
        Items.Add(country3);
        Items.Add(country4);

        SelectedNodes.Add(aus_state1);
        SelectedNodes.Add(aus_state2);
    }        
}
```