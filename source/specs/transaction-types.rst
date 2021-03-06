Transaction Types
=================

There are two kinds of transactions.

Normal type
-----------

Normal transactions are used to transfer tokens and calling smart contracts.

Governance type
----------------

Governance transactions are used for calling system contracts, such as staking and voting.
Transactions of this type have a special payload format and recipient.

The following table shows the specification for each field of the transaction body.

===========  =======  ====================  =================  ==========================================  ==========  ===================
Action       Account  Recipient             Amount             Payload                                     Type        Sign
===========  =======  ====================  =================  ==========================================  ==========  ===================
staking      Sender   :code:`aergo.system`  amount to stake    :code:`s`                                   Governance  Signature of sender
unstaking    "        :code:`aergo.system`  amount to unstake  :code:`u`                                   "           "                  
voting       "        :code:`aergo.system`  0                  :code:`v<peer ids bytes, no separator>`     "           "                  
create name  "        :code:`aergo.name`    1 aergo            :code:`c<name string>`                      "           "                  
update name  "        :code:`aergo.name`    1 aergo            :code:`u<name string>,<new owner address>`  "           "                  
===========  =======  ====================  =================  ==========================================  ==========  ===================