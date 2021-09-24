# rivderpod counter

```dart
final counterProvider = StateNotifierProvider((_) => Counter());

class Counter extends StateNotifier<int> {
  Counter() : super(0);
  void increment() => state++;
}

void main() {
  runApp(
    ProviderScope(
      child: CounterApp(),
    ),
  );
}

class CounterApp extends HookWidget {
  @override
  Widget build(BuildContext context) {
    final state = useProvider(counterProvider.state);
    final counter = useProvider(counterProvider);

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('CounterApp')),
        body: Center(child: Text(state.toString())),
        floatingActionButton: FloatingActionButton(
            onPressed: () => counter.increment(), child: Icon(Icons.add)),
      ),
    );
  }
}
```
