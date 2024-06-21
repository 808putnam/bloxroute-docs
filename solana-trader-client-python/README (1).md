# solana-trader-client-python

You need to install build module to run `python3 -m build` commands.

```python
python3 -m pip install build
```

## Setup Steps

```
# start in solana-trader-client-python
python3 -m venv .venv
source ./.venv/bin/activate
cd ../solana-trader-proto/python
# upgrade version in pyproject.toml
# install twine?
pip3 install -r requirements.txt --no-cache
cd ..
make proto
cd python
pip3 install build
rm -rf dist/ && python3 -m build
pip3 install dist/bxsolana_trader_proto-0.0.69.tar.gz

# Now you can update the depdendency in solana-trader-client-python
# update the version of bxsolana-trader-proto in setup.cfg
# and run 
pip3 install -r requirements.txt
    
# upload - but see notes on using tokens below
python3 -m twine upload --repository pypi dist/*
```

1Password has the id/password for PyPi publishing. Note that you need to use token based authentication - not user id/password. User is something like \_\_\<token>\_\_ and password is \<token>.

Note, there is a .gitsubmodule file in the root folder. However the following commands do not appear to do anything:

```bash
git submodule init
it submodule update
```

