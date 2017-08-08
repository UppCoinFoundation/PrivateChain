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

# set it as the etherbase:
> miner.setEtherbase(personal.listAccounts[0])
true

#start mining
miner.start()
INFO [08-08|11:13:04] Updated mining threads                   threads=0
INFO [08-08|11:13:04] Transaction pool price threshold updated price=18000000000
nullINFO [08-08|11:13:04] Starting mining operation 

> INFO [08-08|11:13:04] Commit new mining work                   number=1 txs=0 uncles=0 elapsed=3.667ms
ERROR[08-08|11:13:06] Failed to generate mapped ethash dataset epoch=0 err="open /Users/User1/.ethash/full-R23-0000000000000000.5577006791947779410: permission denied"
