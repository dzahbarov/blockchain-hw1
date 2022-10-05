## Task 1

```
@@ -190,6 +190,7 @@ contract MultiSigWallet {
         public
         returns (uint transactionId)
     {
+        require(value <= 66 ether);
         transactionId = addTransaction(destination, value, data);
         confirmTransaction(transactionId);
     }
```

## Task 2
```
@@ -230,6 +230,7 @@ contract ERC20 is Context, IERC20, IERC20Metadata {
     ) internal virtual {
         require(from != address(0), "ERC20: transfer from the zero address");
         require(to != address(0), "ERC20: transfer to the zero address");
+        require((block.timestamp % (1 days) + 3) % 7 != 5, "saturday transfer");

         _beforeTokenTransfer(from, to, amount);
```

## Task 3
```
@@ -37,7 +37,7 @@ contract DividendToken is StandardToken, Ownable {
         }));
     }

-    function() external payable {
+    function deposit(bytes[32] comment) external payable {
         if (msg.value > 0) {
             emit Deposit(msg.sender, msg.value);
             m_totalDividends = m_totalDividends.add(msg.value);
```
