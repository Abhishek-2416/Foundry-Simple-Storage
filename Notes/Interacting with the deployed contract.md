Now that we actually have deployed a contract we should learn how to interact with them in the same way we do with remix
There are two methods of doing it 

**Better pratices for just deployment testing 
  Instead of entering the rpc url and privatekey again and again 
  we can first create an env file and store rpc and privatekey
  after this type source .env in cli 
  then use $PRIVATE_KEY and $RPC_URL to access them
  This also isnt safe so the best pratice is to ecrypt the env

1.Using Command line
  Here we need to use the send , which takes arguments the address the signature(which here is the function type and uint type) and the arguments or value we need to pass

  The Cast send is used to sign and publish the transaction

  **cast send 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 "store(uint256)" 123 --rpc-url $RPC_URL --private-key $PRIVATE_KEY**

  which will provide us with :-

  blockHash               0xc62fcdb1384c252001b944903020e985f8a762c8ba1f92f03c99369e1d918bb9
  blockNumber             4
  contractAddress         
  cumulativeGasUsed       21204
  effectiveGasPrice       3674622424
  gasUsed                 21204
  logs                    []
  logsBloom               0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
  root                    
  status                  1
  transactionHash         0xfb0ccd17cc249aa80da1b5fadaef9be7158cbe62d395ca4bf2a3290ffe4baa94
  transactionIndex        0
  type                    2

  Now to read this we need to type "cast call" which takes the arguments exact same as "cast send"

  **cast call "CONTRACT ADDRESS" "function name"**

  this will provide us in hex code again so we again need to run the command 

  **cast --to-base 0x714e1 dec this will convert hexadecimal to decimal so we get 464097**
  

  