# Flutter-Cheatsheet

**Font and Theme  setup**
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "My EXP App",
      theme: ThemeData(
          primarySwatch: Colors.purple,
          accentColor: Colors.amber,
          fontFamily: 'Quicksand',
          textTheme: ThemeData.light().textTheme.copyWith(
                  title: TextStyle(
                fontFamily: 'OpenSans',
                fontSize: 18,
              )),
          appBarTheme: AppBarTheme(
              textTheme: ThemeData.light().textTheme.copyWith(
                      title: TextStyle(
                    fontFamily: 'OpenSans',
                    fontSize: 20,
                    fontWeight: FontWeight.bold,
                  )))),
      home: MyHomePage(),
    );
  }
  
**Show Modal**  
showModalBottomSheet(
	context: context,
	builder: (bCtx) {
	  return NewTransaction(
		addTransaction: _addNewTransaction,
	  );
	}); 

**Manipulate list**
List<Transaction> get _recentTransactions {
return transactions.where((tx) {
  return tx.date.isAfter(DateTime.now().subtract(Duration(
	days: 7,
  )));
}).toList();
}

**Floating Action Button**
floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
floatingActionButton: FloatingActionButton(
child: Icon(Icons.add),
onPressed: () {
  _startAddNewTransaction(context);
},


**Generating List**
return List.generate(7, (index) {
final weekday = DateTime.now().subtract(Duration(days: index));
var totalSum = 0.0;

return {'day': DateFormat.E().format(weekday), 'amount': totalSum};
}).reversed.toList()


**Fractionally Sized Box**
FractionallySizedBox(
	heightFactor: spendPCTAmount,
	child: Container(
	  decoration: BoxDecoration(
		color: Theme.of(context).primaryColor,
		borderRadius: BorderRadius.circular(10),
	  ),
	),
 )
 
 
**Theme**
Theme.of(context).accentColor
Theme.of(context).primaryColor
Theme.of(context).textTheme.title

**TextField shift focus**
onEditingComplete: () => FocusScope.of(context).nextFocus()


**Date Picker**
void _showPresentDatePicker() {
showDatePicker(
  context: context,
  initialDate: DateTime.now(),
  firstDate: DateTime(2019),
  lastDate: DateTime.now(),
).then((pickedDate) {
  if (pickedDate == null) {
	return;
  }
  setState(() {
	_selectedDate = pickedDate;
  });
});
}


**Add Image**
Image.asset('assets/images/waiting.png',fit: BoxFit.cover,)

**Icon Button	**
IconButton(
  icon: Icon(Icons.delete),
  color: Colors.red,
  onPressed: () {
	deleteTx(transactions[index].id);
  },
),
