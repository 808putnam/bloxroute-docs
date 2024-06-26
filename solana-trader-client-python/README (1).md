# solana-trader-client-python

## Local development

<pre><code># Start in solana-trader-client-python and create a
# virtual environment for solana-trader-client-python
python3 -m venv .venv
source ./.venv/bin/activate

# Install build/publish packages into 
# solana-trader-client-python's venv
python3 -m pip install --upgrade build
python3 -m pip install --upgrade twine

# Assumes we have solana-trader-proto as sibling folder.
# Update submodule for solana-trader-proto
cd ../solana-trader-proto
git submodule init
git submodule update

# IMPORTANT: Not shown - upgrade 'version' field in 
#            solana-trader-proto/pthon/ppyproject.toml

# Install solana-trader-proto requirements into 
# solana-trader-client-python's venv. This will install the
# proto builder for python library.
cd python
pip3 install -r requirements.txt --no-cache

# Output our proto files for python 
cd ..
make proto

# Build a local version of solana-trader-proto
cd python
rm -rf dist/ &#x26;&#x26; python3 -m build

# Install the the local build of solana-trader-proto into
# solana-trader-client-python's venv
<strong>pip3 install dist/bxsolana_trader_proto-0.0.70.tar.gz
</strong>
# IMPORTANT: Not shown - update version for the depdendency for 
#            bxsolana-trader-proto in solana-trader-client-python/setup.cfg.

# Install the remainder of the requirements for solana-trader-client-python int
# solana-trader-client-python's venv.
cd ../../solana-trader-client-python
pip3 install -r requirements.txt
</code></pre>

## Publishing

1Password has the token for PyPi publishing. Note that you need to use token based authentication - not user id/password.&#x20;

These steps assume:

1. You are in develop branch for both solana-trader-proto and solana-trader-python with all changes merged in.
2. The pyproject.toml version field for solana-trader-proto has been udpated to the new version for the solana-trader-proto library.
3. The solana-trader-proto version you refernce in setup.cfg has been published to PyPI.
4. The setup.cfg version field has been updated to the new version for the solana-trader-client-python library you are publishing.

For publishing, you will be prompted for a username and password. For the username, use `__token__`. For the password, use the token value from 1Password, including the `pypi-` prefix.

```
# Start in solana-trader-client-python and create a
# virtual environment for solana-trader-client-python
python3 -m venv .venv
source ./.venv/bin/activate

# Install build/publish packages and requirements into 
# solana-trader-client-python's venv
python3 -m pip install --upgrade build
python3 -m pip install --upgrade twine
pip3 install -r requirements.txt

# Assumes we have solana-trader-proto as sibling folder.
# Update submodule for solana-trader-proto
cd ../solana-trader-proto
git submodule init
git submodule update

# Install solana-trader-proto requirements into 
# solana-trader-client-python's venv. This will install the
# proto builder for python library.
cd python
pip3 install -r requirements.txt --no-cache

# Output our proto files for python 
cd ..
make proto

# Build a local version of solana-trader-proto
cd python
rm -rf dist/ && python3 -m build

# Publish local version of solana-trader-proto to pypi
python3 -m twine upload --repository pypi dist/*

# Build a local version of solana-trader-client-python
cd ../../solana-trader-client-python
rm -rf dist/ && python3 -m build

# Publish local version of solana-trader-client-python to pypi
python3 -m twine upload --repository pypi dist/*
```

After the publishing commands complete, you should see output similar to this:

```
Uploading distributions to https://pypi.org/legacy/
Enter your username: __token__
Uploading example_package_YOUR_USERNAME_HERE-0.0.1-py3-none-any.whl
100% ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 8.2/8.2 kB • 00:01 • ?
Uploading example_package_YOUR_USERNAME_HERE-0.0.1.tar.gz
100% ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 6.8/6.8 kB • 00:00 • ?
```

Once uploaded, your package should be viewable on PyPI. For example:&#x20;

`https://pypi.org/project/example_package_YOUR_USERNAME_HERE`

## Additional Notes

Note, there is a .gitsubmodule file in the root folder. However the following commands do not appear to do anything:

```bash
git submodule init
it submodule update
```

