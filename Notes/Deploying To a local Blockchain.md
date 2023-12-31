This is where we learn how to deploy to a local  blockchain using foundry, There are 2 ways to do so 

1. Command line
   The first way is by doing it using command line

   **forge create (name of the contract) --rpc-url http://127.0.0.1:8545 --private-key (Enter the private key)**

   Things that we should avoid pasting up our private key in plain text can be big big mistake so never do it with real account
   
   CLEAR ZSH HISTORY
   Also clear history in zsh by "history -c"
   
2. The second way to deploy a contract is by writing scripts,when we are deploying our code we want to make sure we have a continous reproducable way to deploy our smart contracts

And when we test the our code in future we want to test our code in future , we want it to test our deployments processes as well as the code
Solidity as contract language and Solidity as scripting language are different,Foundry has built in stuff which gives solidity even more functionality outside just smart contracts

After we have written the script we need to type in cli 

** forge script script/DeploySimpleStorage.s.sol ** 

Here we might ask we dont have local blockchain running so where does it deploy to,
In Foundry if we dont specify and RPC it will automatically deploy on temporary anvil blockchain

And if we type 

**forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545**

If we just do this and it will complete Simulation 
By doing this we get new folder named brodcast which gives information about our previous deployments

Now if we completely want to deploy it we should type in the command line

**forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key (Enter the private key)**

ONCHAIN EXECUTION COMPLETE AND SUCCESSFULL


The run.json files contain all details about the transaction hash contractName etc
"transaction": {
        "type": "0x02",
        "from": "0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266",
        "gas": "0x714e1",
        "value": "0x0",
        "data": "0x608060405234801561001057600080fd5b5061057f806100206000396000f3fe608060405234801561001057600080fd5b50600436106100575760003560e01c80632e64cec11461005c5780632ebce631146100735780636057361d146100945780636f760f41146100a95780638bab8dd5146100bc575b600080fd5b6000545b6040519081526020015b60405180910390f35b610086610081366004610248565b6100e7565b60405161006a929190610285565b6100a76100a2366004610248565b600055565b005b6100a76100b7366004610362565b61019f565b6100606100ca3660046103a7565b805160208183018101805160028252928201919093012091525481565b600181815481106100f757600080fd5b6000918252602090912060029091020180546001820180549193509061011c906103e4565b80601f0160208091040260200160405190810160405280929190818152602001828054610148906103e4565b80156101955780601f1061016a57610100808354040283529160200191610195565b820191906000526020600020905b81548152906001019060200180831161017857829003601f168201915b5050505050905082565b6040805180820190915281815260208101838152600180548082018255600091909152825160029091027fb10e2d527612073b26eecdfd717e6a320cf44b4afac2b0732d9fcbe2b7fa0cf68101918255915190917fb10e2d527612073b26eecdfd717e6a320cf44b4afac2b0732d9fcbe2b7fa0cf70190610220908261046d565b50505080600283604051610234919061052d565b908152604051908190036020019020555050565b60006020828403121561025a57600080fd5b5035919050565b60005b8381101561027c578181015183820152602001610264565b50506000910152565b82815260406020820152600082518060408401526102aa816060850160208701610261565b601f01601f1916919091016060019392505050565b634e487b7160e01b600052604160045260246000fd5b600082601f8301126102e657600080fd5b813567ffffffffffffffff80821115610301576103016102bf565b604051601f8301601f19908116603f01168101908282118183101715610329576103296102bf565b8160405283815286602085880101111561034257600080fd5b836020870160208301376000602085830101528094505050505092915050565b6000806040838503121561037557600080fd5b823567ffffffffffffffff81111561038c57600080fd5b610398858286016102d5565b95602094909401359450505050565b6000602082840312156103b957600080fd5b813567ffffffffffffffff8111156103d057600080fd5b6103dc848285016102d5565b949350505050565b600181811c908216806103f857607f821691505b60208210810361041857634e487b7160e01b600052602260045260246000fd5b50919050565b601f82111561046857600081815260208120601f850160051c810160208610156104455750805b601f850160051c820191505b8181101561046457828155600101610451565b5050505b505050565b815167ffffffffffffffff811115610487576104876102bf565b61049b8161049584546103e4565b8461041e565b602080601f8311600181146104d057600084156104b85750858301515b600019600386901b1c1916600185901b178555610464565b600085815260208120601f198616915b828110156104ff578886015182559484019460019091019084016104e0565b508582101561051d5787850151600019600388901b60f8161c191681555b5050505050600190811b01905550565b6000825161053f818460208701610261565b919091019291505056fea2646970667358221220e6693aadd6bf6ec591e14d54396b0871db5ef14d8b89869e01b0996de72f4e4964736f6c63430008130033",
        "nonce": "0x1",
        "accessList": []
      }
      we need our private key to actually sign transaction that we build and then sending it
Whenever we do forge script or forge create this the data we are actually sending to the rpc

As we can see here the gas value is 0x714e1 which is in hexadecimal so this is easiest method to convert this hexadecimal value
In cli type 

**cast --to-base 0x714e1 dec this will convert hexadecimal to decimal so we get 464097**


3. To deploy the contract without revealing the private key 
    
   - First we need to use the command **cast wallet import defaultKey --interactive** Here then we need to enter the private key and the password
   - Then to use the private key secretly without revealing anything we need to type 
   - **forge script script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --account defaultKey --sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266       --broadcast -vvvv**
   - 