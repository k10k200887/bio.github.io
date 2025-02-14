// Set up RecyclerView in the WalletActivity to display transactions
RecyclerView recyclerView = findViewById(R.id.recyclerView);
TransactionAdapter adapter = new TransactionAdapter(transactionHistory);
recyclerView.setLayoutManager(new LinearLayoutManager(this));
recyclerView.setAdapter(adapter);