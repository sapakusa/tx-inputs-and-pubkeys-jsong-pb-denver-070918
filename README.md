
# Inputs and pubkeys [NOT WORKING]


```python
# Example of how to look up a transaction using fetch_tx() method

from tx import TxIn

prev_tx = bytes.fromhex('d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81') 
tx_in = TxIn(prev_tx, 0, b'', 0xffffffff)
print(tx_in.fetch_tx())
```

### Exercise


#### What is the value and scriptPubKey of the 0th output of this transaction?
```
d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81
```


```python
# Exercise 4.1

from tx import TxIn

prev_tx = bytes.fromhex('d1c789a9c60383bf715f3f6ad9d14b91fe55f3deb369fe5d9280cb1a01793f81') 
prev_index = 0

# create the transaction input (use blank script_sig and 0xffffffff for sequence)
# fetch the transaction
# grab the output at the index
# show the amount
# show the script_pubkey
```

### Test Driven Exercise


#### Bonus:
#### Cache the requests so that you don't hit blockcypher.com multiple times for the same transaction output.


```python
from tx import TxIn

class TxIn(TxIn):

    def value(self, testnet=False):
        '''Get the outpoint value by looking up the tx hash on libbitcoin server
        Returns the amount in satoshi
        '''
        # use self.fetch_tx to get the transaction
        # get the output at self.prev_index
        # return the amount property
        pass

    def script_pubkey(self, testnet=False):
        '''Get the scriptPubKey by looking up the tx hash on libbitcoin server
        Returns the binary scriptpubkey
        '''
        # use self.fetch_tx to get the transaction
        # get the output at self.prev_index
        # return the script_pubkey property
        pass
```
