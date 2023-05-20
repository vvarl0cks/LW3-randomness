# 🤫 A cautionary tale to never use on-chain randomness

Randomness is a hard problem. Computers run code that is written by programmers, and follows a given sequence of steps. As such, it is extremely hard to design an algorithm that will give you a 'random' number, since that random number must be coming from an algorithm that follows a certain sequence of steps. Now, of course, some functions are better than others.

```shell
gitpod /workspace/LW3-randomness (main) $ npx hardhat test
Compiled 3 Solidity files successfully


  Attack
Game contract address 0x5FbDB2315678afecb367f032d93F642f64180aa3
Attack contract address 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512
    ✔ Should be able to guess the exact number (1106ms)

  Lock
    Deployment
      ✔ Should set the right unlockTime (46ms)
      ✔ Should set the right owner
      ✔ Should receive and store the funds to lock
      ✔ Should fail if the unlockTime is not in the future
    Withdrawals
      Validations
        ✔ Should revert with the right error if called too soon
        ✔ Should revert with the right error if called from another account
        ✔ Shouldn't fail if the unlockTime has arrived and the owner calls it
      Events
        ✔ Should emit an event on withdrawals
      Transfers
        ✔ Should transfer the funds to the owner


  10 passing (1s)
```
# 👮 Preventions
- Don't use blockhash, block.timestamp, or really any sort of on-chain data as sources of randomness
- You can use Chainlink VRF's for true source of randomness ➡ https://docs.chain.link/docs/chainlink-vrf/
