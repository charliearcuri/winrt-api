---
-api-id: M:Windows.ApplicationModel.Search.SearchPane.SetLocalContentSuggestionSettings(Windows.ApplicationModel.Search.LocalContentSuggestionSettings)
-api-type: winrt method
---

<!-- Method syntax
public void SetLocalContentSuggestionSettings(Windows.ApplicationModel.Search.LocalContentSuggestionSettings settings)
-->

# Windows.ApplicationModel.Search.SearchPane.SetLocalContentSuggestionSettings

## -description
Specifies whether suggestions based on local files are automatically displayed in the search pane, and defines the criteria that Windows uses to locate and filter these suggestions.

## -parameters
### -param settings
The new settings for local content suggestions.

## -remarks
> [!NOTE]
> An app can't use both the search box ([Windows.UI.Xaml.Controls.SearchBox](../windows.ui.xaml.controls/searchbox.md) for Windows Store app using C++, C#, or Visual Basic, [WinJS.UI.SearchBox](http://msdn.microsoft.com/library/58f5cea3-a19b-48a8-abcc-17f38d8fa886) for Windows app using JavaScript) and the [SearchPane](searchpane.md). Using both the search box and the search pane in the same app causes the app to throw an exception with this message: "Cannot create instance of type 'Windows.UI.Xaml.Controls.SearchBox.'"

When local content suggestions are enabled, Windows will provide search suggestions from the user's local files as the user enters query text. For example, a picture application can configure local content suggestions so that search suggestions come only from a particular kind of image file that is stored in the user's picture library.




## -examples
The [Search contract sample](http://go.microsoft.com/fwlink/p/?linkid=234892) demonstrates how to customize local suggestions by restricting the locations and kinds of files that the suggestions are based on.

> [!TIP]
> You should add this code to your app's global scope and run it as soon as your app is launched.

```csharp
// Have Windows provide suggestions from local files.
// This code should be placed in your apps global scope and run as soon as your app is launched.
var settings = new LocalContentSuggestionSettings();
settings.Enabled = true;
if (isLocal)
{
    settings.Locations.Add(KnownFolders.MusicLibrary);
    settings.AqsFilter = "kind:Music";
}
SearchPane.GetForCurrentView().SetLocalContentSuggestionSettings(settings);
```

```javascript
var settings = new Windows.ApplicationModel.Search.LocalContentSuggestionSettings();
settings.enabled = true;
settings.locations.append(Windows.Storage.KnownFolders.musicLibrary);
settings.aqsFilter = "kind:=music";

Windows.ApplicationModel.Search.SearchPane.getForCurrentView().setLocalContentSuggestionSettings(settings);
```

In the example, suggestions are restricted to one kind of file, music files, using an Advanced Query Syntax (AQS) string. Two of the most common Advanced Query Syntax (AQS) filters restrict based on file kind, like "kind:=.music" in the example; and based on file name extension, like "ext:=.mp3". You can learn more about AQS in [Advanced Query Syntax (AQS)](https://msdn.microsoft.com/en-us/library/aa965711.aspx).

## -see-also
[](http://msdn.microsoft.com/library/8e55bd40-c7cf-44a6-bc18-24bc7a267779), [Quickstart: Adding search](http://msdn.microsoft.com/library/d412c562-22d2-41c4-9f27-27503b89b9e9), [Search contract sample](http://go.microsoft.com/fwlink/p/?linkid=234892), [LocalContentSuggestionSettings class](localcontentsuggestionsettings.md), [SearchPane class](searchpane.md)