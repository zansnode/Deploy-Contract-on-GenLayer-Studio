## GenLayer How to Deploy Your First Intelligent Contract

Hey! This is a quick and easy guide to deploy an Intelligent Contract on GenLayer using GenLayer Studio and the CLI.Intelligent Contracts are written in Python and can do cool AI stuff — like fetching news, analyzing sentiment, or making decisions based on real-world data.

-----

## Requirements
- Go to [Studio GenLayer](https://studio.genlayer.com)
- Connect to Testnet Bradbury (choose it from the network dropdown)
- Get some free test GEN tokens from [Testnet Faucet GenLayer](https://testnet-faucet.genlayer.foundation/)

(Optional) Install the GenLayer CLI:
`pip install genlayer`

-----

#### Method 1: Deploy Using GenLayer Studio
1. Open GenLayer Studio and make sure you're on Testnet Bradbury.
2. Click New Contract (or the "+" icon).
3. Give it a name, for example: ``my_first_contract.py``
4. Paste your contract code into the editor.
5. On the left side, fill in the **Constructor Inputs** if your contract has any (if none, just leave it empty).
6. Click the big Deploy button.
7. Wait until the status says Finalized (usually takes 30–60 seconds).
8. Copy the Contract Address and Transaction Hash — you’ll need them!
Done! Your contract is now live on the testnet.


#### Method 2: Deploy Using CLI (Quick Command Line Way)

```
# Simple deployment
genlayer deploy --contract contracts/my_contract.py --network testnet
# If your contract needs constructor arguments
genlayer deploy --contract contracts/my_contract.py --args "Initial Greeting" 100 --network testnet``
```

-----

#### Simple Example Contract (Counter)
Create a file called `counter.py`:

```
# { "Depends": "py-genlayer:latest" }

from genlayer import *

class Counter(gl.Contract):
    count: int

    def __init__(self, initial_count: int = 0):
        self.count = initial_count

    @gl.public.view
    def get_count(self) -> int:
        return self.count

    @gl.public.write
    def increment(self):
        self.count += 1

    @gl.public.write
    def decrement(self):
        if self.count > 0:
            self.count -= 1
```

-----

#### How to Interact With Your Contract
After deploying:

- Use Write methods to change data (like `increment` or `analyze_sentiment`).
- Use View methods to read data (like `get_count` or `get_sentiment`).
- In GenLayer Studio, you can test everything directly after deployment.

------

#### Quick Tips

- Always test your contract in Studio first.
- If validators don’t agree the first time, just retry — it usually works on the second try.
- Use `check_bullish` when you want faster results.
- Keep your contract address safe and document it in your repo.

#### Troubleshooting

- Deployment fails? → Check you have enough test GEN and the right network.
- Constructor error? → Make sure the parameters match what you wrote in `__init__`.
- Method not showing? → Add `@gl.public.view` or `@gl.public.write.`

#### Usefull Links

- [Docs GenLayer](https://docs.genlayer.com)
- [GenLayer Studio](https://studio.genlayer.com)
- CLI Docs: Check the GenLayer documentation




