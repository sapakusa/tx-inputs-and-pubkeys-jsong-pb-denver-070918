
# Looking Up Transactions


```python
# Example of how to look up a transaction using fetch_tx() method

from tx import TxIn
prev_tx = bytes.fromhex('d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81') 
tx_in = TxIn(prev_tx, 0, b'', 0xffffffff)
print(tx_in.fetch_tx())
```

### Try it


#### What is the value and scriptPubKey of the 0th output of this transaction?
```
d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81
```


```python
from tx import TxIn

prev_tx = bytes.fromhex('d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81') 
prev_index = 0

# create the transaction input (use blank script_sig and 0xffffffff for sequence)
tx_in = TxIn(prev_tx, 0, b'', 0xffffffff)
# fetch the transaction
t = tx_in.fetch_tx()
# grab the output at the index
prev_output = t.tx_outs[prev_index]
# show the amount
print(prev_output.amount)
# show the script_pubkey
print(prev_output.script_pubkey)
```

### Test Driven Exercise


```python
from tx import TxIn

class TxIn(TxIn):

    def value(self, testnet=False):
        '''Get the outpoint value by looking up the tx hash on libbitcoin server
        Returns the amount in satoshi
        '''
        # use self.fetch_tx to get the transaction
        tx = self.fetch_tx(testnet=testnet)
        # get the output at self.prev_index
        # return the amount property
        return tx.tx_outs[self.prev_index].amount

    def script_pubkey(self, testnet=False):
        '''Get the scriptPubKey by looking up the tx hash on libbitcoin server
        Returns the binary scriptpubkey
        '''
        # use self.fetch_tx to get the transaction
        tx = self.fetch_tx(testnet=testnet)
        # get the output at self.prev_index
        # return the script_pubkey property and serialize
        return tx.tx_outs[self.prev_index].script_pubkey
```
