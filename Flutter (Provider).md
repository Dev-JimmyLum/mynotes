## Flutter (Provider)

Provider has several commonly used classes that you’ll learn about in more detail: 
ChangeNotifierProvider, Consumer, FutureProvider, MultiProvider and 
StreamProvider



### ChangeNotifier

ChangeNotifier is a class that adds and removes listeners, then notifies those 
listeners of any changes. You usually extend the class for models so you can send 
notifications when your model changes.

```dart
class CartModel extends ChangeNotifier {
  /// The private fiel}d backing [catalog].
  late CatalogModel _catalog;

  /// Internal, private state of the cart. Stores the ids of each item.
  final List<int> _itemIds = [];

  /// The current catalog. Used to construct items from numeric ids.
  CatalogModel get catalog => _catalog;

  set catalog(CatalogModel newCatalog) {
    _catalog = newCatalog;
    // Notify listeners, in case the new catalog provides information
    // different from the previous one. For example, availability of an item
    // might have changed.
    notifyListeners();
isteners();
  }
}
```

### ChangeNotifierProvider

ChangeNotifierProvider is a widget that wraps a class, implementing 
ChangeNotifier and uses the child widget for display. When changes are broadcast, 
the widget rebuilds its tree

```dart
void main() {
  runApp(
    // Provide the model to all widgets within the app. We're using
    // ChangeNotifierProvider because that's a simple way to rebuild
    // widgets when a model changes. We could also just use
    // Provider, but then we would have to listen to Counter ourselves.
    //
    // Read Provider's docs to learn about all the available providers.
    ChangeNotifierProvider(
      // Initialize the model in the builder. That way, Provider
      // can own Counter's lifecycle, making sure to call `dispose`
      // when not needed anymore.
      create: (context) => Counter(),
      child: const MyApp(),
    ),
  );
}
```

### Consumer

Consumer is a widget that listens for changes in a class that implements 
ChangeNotifier, then rebuilds the widgets below itself when it finds any. When 
building your widget tree, try to put a Consumer as deep as possible in the UI 
hierarchy, so updates don’t recreate the whole widget tree

```dart
Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Flutter Demo Home Page'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text('You have pushed the button this many times:'),
            // Consumer looks for an ancestor Provider widget
            // and retrieves its model (Counter, in this case).
            // Then it uses that model to build widgets, and will trigger
            // rebuilds if the model is updated.
            Consumer<Counter>(
              builder: (context, counter, child) => Text(
                '${counter.value}',
                style: Theme.of(context).textTheme.headline4,
              ),
            ),
          ],
        ),
      ),
```

### FutureProvider

FutureProvider works like other providers and uses the required create parameter 
that returns a Future



### StreamProvider






