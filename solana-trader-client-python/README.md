# solana-trader-python

Note, there is a .gitsubmodule file in the root folder. However the following commands do not appear to do anything:

```bash
git submodule init
it submodule update --recursive --depth 1
```

## nautilus\_trader modifications

### Poetry notes

To add a new python dependency:

```bash
poetry add <dependency>
```

if you change a version of dependence p

```bash
poetry lock --no update
```

### Modifications

1. Dropped to python 3.10 due to aiohttp not building
2. Dropped to docformatter 1.5.0&#x20;

```bash
Because no versions of bxsolana-trader match >2.1.0,<3.0.0 and bxsolana-trader (2.1.0) depends on aiohttp (3.8.1), bxsolana-trader (>=2.1.0,<3.0.0) requires aiohttp (3.8.1).
And because aiohttp (3.8.1) depends on charset-normalizer (>=2.0,<3.0), bxsolana-trader (>=2.1.0,<3.0.0) requires charset-normalizer (>=2.0,<3.0).
bxsolana aiohttp charset-normalizer (2-3)
docformatter charsetnormalizer (3-4)
And because docformatter (1.7.5) depends on charset_normalizer (>=3.0.0,<4.0.0) and no versions of docformatter match >1.7.5,<2.0.0, bxsolana-trader (>=2.1.0,<3.0.0) is incompatible with docformatter (>=1.7.5,<2.0.0).

```

So, because nautilus-trader depends on both bxsolana-trader (^2.1.0) and docformatter (^1.7.5), version solving failed.

3. Added commented sections `qtrade: bloxroute` to:
   1. pyproject.toml
   2. examples/live/qtrade/qtrade\_arbitrage\_strategy

```
2TMkPK6bn3YkEyHXTg79B8MH7gw4bD29Dhv4eBXr4D6joSCeT2rDfSXAPBXTBfyAFq56LTR137faFT8GtRcBGYC8
5tyTZiNUuymMoSsdHtfyqHVHELiSUJmafHMfZg7RqxtX
Ko64NSYFCqstSbQCHSxmTKrgTZURHVjaR2SDuxzREjr
```