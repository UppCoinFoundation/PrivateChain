#UppCoin

# Installation of geth on command line MAC
brew update
brew upgrade
brew tap ethereum/ethereum
brew install ethereum
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.ethereum.plist
brew install solidity

# PrivateChain
# Launching geth & initialising genesis block

geth --identity "Princess" --rpc --rpcport "8080" --rpccorsdomain "*" --datadir "/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development" --port "30303" --nodiscover --rpcapi "db,eth,net,web3" --networkid 1987 init /Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/CustomGenesis.json
WARN [08-08|09:48:29] No etherbase set and no accounts found as default 
INFO [08-08|09:48:29] Allocated cache and file handles         database=/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/geth/chaindata cache=16 handles=16
INFO [08-08|09:48:29] Writing custom genesis block 
INFO [08-08|09:48:29] Successfully wrote genesis state         database=chaindata                                                                        hash=6650a0…b5c158
INFO [08-08|09:48:29] Allocated cache and file handles         database=/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/geth/lightchaindata cache=16 handles=16
INFO [08-08|09:48:29] Writing custom genesis block 
INFO [08-08|09:48:29] Successfully wrote genesis state         database=lightchaindata                                                                        hash=6650a0…b5c1

>>>
 geth --identity "Princess" --rpc --rpcport "8080" --rpccorsdomain "*" --datadir "/Users/User1/Library/Ethereum" --port "21000" --nodiscover --rpcapi "db,eth,net,web3" --networkid 1987 init /Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/CustomGenesis.json
 
# To interact with geth through the console
geth --identity "Princess" --rpc --rpcport "8080" --rpccorsdomain "*" --datadir "/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development" --port "8443" --nodiscover --rpcapi "db,eth,net,web3" --networkid 1987 console

WARN [08-08|10:08:15] No etherbase set and no accounts found as default 
INFO [08-08|10:08:15] Starting peer-to-peer node               instance=Geth/Princess/v1.7.0-unstable-97107982/darwin-amd64/go1.8.3
INFO [08-08|10:08:15] Allocated cache and file handles         database=/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/geth/chaindata cache=128 handles=1024
INFO [08-08|10:08:15] Initialised chain configuration          config="{ChainID: 1987 Homestead: 0 DAO: <nil> DAOSupport: false EIP150: <nil> EIP155: 0 EIP158: 0 Metropolis: <nil> Engine: unknown}"
INFO [08-08|10:08:15] Disk storage enabled for ethash caches   dir=/Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/geth/ethash count=3
INFO [08-08|10:08:15] Disk storage enabled for ethash DAGs     dir=/Users/User1/.ethash                                                          count=2
INFO [08-08|10:08:15] Initialising Ethereum protocol           versions="[63 62]" network=1987
INFO [08-08|10:08:15] Loaded most recent local header          number=0 hash=6650a0…b5c158 td=1024
INFO [08-08|10:08:15] Loaded most recent local full block      number=0 hash=6650a0…b5c158 td=1024
INFO [08-08|10:08:15] Loaded most recent local fast block      number=0 hash=6650a0…b5c158 td=1024
INFO [08-08|10:08:15] Loaded local transaction journal         transactions=0 dropped=0
INFO [08-08|10:08:15] Regenerated local transaction journal    transactions=0 accounts=0
INFO [08-08|10:08:15] Starting P2P networking 
INFO [08-08|10:08:15] RLPx listener up                         self="enode://4e8b190c0cb2dbcf69783fd1c098b36bc130bfa22edbf8e6f78ae6769c30705c95b43b88830d55c17c8e3232f35ec2481c527baefabadf9b24b937da82f70d25@[::]:8443?discport=0"
INFO [08-08|10:08:15] IPC endpoint opened: /Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/geth.ipc 
INFO [08-08|10:08:15] HTTP endpoint opened: http://127.0.0.1:8080 
Welcome to the Geth JavaScript console!

instance: Geth/Princess/v1.7.0-unstable-97107982/darwin-amd64/go1.8.3
 modules: admin:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0
 
# initialize a new account on the testnest, to set it as your etherbase (the address that will receive mining rewards).
> personal.newAccount("password")
INFO [08-08|11:10:02] New wallet appeared                      url=keystore:///Users/User1/Desktop… status=Locked
"0x3ba67f916972127adee3e1349ca23dc4e6637901"

INFO [08-08|11:10:02] New wallet appeared                      url=keystore:///Users/User1/Desktop… status=Locked
"0x53254ce5fecc835c6c8925819e6bee417ea25d46"

#To add new wallet to the Custom Genesis file, adjust alloc settings & reinitate genesis file 

# set it as the etherbase:
> miner.setEtherbase(personal.listAccounts[0])
true

#copy new accounts to ethereum folder; separate terminal instance
cp /Users/User1/Desktop/extras/UppCoinFoundation/UppCoin_Development/keystore/UTC--2017-08-0* ~/Library/Ethereum/keystore/

# Take note of which account # is the one that you pre-allocated ether to
# return account addresses you possess.
> eth.accounts
["0x3ba67f916972127adee3e1349ca23dc4e6637901", "0x53254ce5fecc835c6c8925819e6bee417ea25d46"]

#set primary account 
>  primary = eth.accounts[0]
"0x3ba67f916972127adee3e1349ca23dc4e6637901"

#check balance
> balance = web3.fromWei(eth.getBalance(primary), "ether");
705


#start mining
miner.start()

> miner.start()
INFO [08-10|13:09:25] Updated mining threads                   threads=0
INFO [08-10|13:09:25] Transaction pool price threshold updated price=0
INFO [08-10|13:09:25] Starting mining operation 
null
> INFO [08-10|13:09:25] Commit new mining work                   number=1 txs=0 uncles=0 elapsed=277.064
INFO [08-10|13:09:25] Generating DAG in progress               epoch=1 percentage=98 elapsed=9.826ms
INFO [08-10|13:09:25] Generating DAG in progress               epoch=1 percentage=99 elapsed=9.929ms
INFO [08-10|13:09:25] Successfully sealed new block            number=1 hash=ef3764…6407f6
INFO [08-10|13:09:25] 🔨 mined potential block                  number=1 hash=ef3764…6407f6
INFO [08-10|13:09:25] Commit new mining work                   number=2 txs=0 uncles=0 elapsed=620.408µs

