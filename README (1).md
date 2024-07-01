# solana-trader-proto



```
# assumes you are in root of solana-trader-proto
git submodule init
git submodule update
cd python

# note, .gitignore needs to be udpated to exclude .venv folder
python3 -m venv .venv
source ./.venv/bin/activate
python3 -m pip install --upgrade build
python3 -m pip install --upgrade twine
pip3 install -r requirements.txt --no-cache

# you should not receive that error message about optional fields now
cd ..
make proto

cd python
rm -rf dist/ && python3 -m build
python3 -m twine upload --repository pypi -u __token__ -p pypi-AgEIcHlwaS5vcmcCJDUwNmVlNTMyLTM3NWQtNGE5MS1hMWQyLTFiZGEzMmM5ZTM3OAACKlszLCIwNDg3NTQwZS1mNTMyLTQxNmMtYmM0Ni02ZjY2NTk4OWUyMDYiXQAABiA_B5srlA6yGWg1CVpkEYUa3WlyAAWcxWrTixMvE1uIfQ --verbose dist/*

```

Note, there is a .gitsubmodule file in the root folder. Use the the following commands to pull in the mev-protos submodule:

```bash
git submodule init
git submodule update 
```

You need to install build module to run `python3 -m build` commands.

```python
python3 -m pip install build
```

## How to point go sdk and trader api to new instances of solana-trader-proto

* If the changes are still local and you have not committed, you can use the replace command in the appropriate go.mod (go sdk or trader api) to point to the folder location that holds the go.mod for solana-trader.proto.
* If the changes are in a commit that has been pushed in a branch, then you can you can do\
  \
  `go get github.com/bloXroute-Labs/solana-trader-proto@<yourlatestcommit>`    \
  \
  in solana-trader-api or solana-trader-client-go while you are doing development, then run \
  \
  `go mod tidy`\
  \


