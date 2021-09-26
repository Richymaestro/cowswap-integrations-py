# CowSwap API Integrations & Tid Bits

A collection of python scripts and services built as simple integrations
with [Gnosis Protocol v2](https://gnosis.io/protocol/)

## Trading Bot for Stable Coin Orders

Initially inspired by [Martin's script](https://pastebin.com/RZyfL08P). This integration
is a simple bot which monitors the orderbook seeking open orders
between [stable coins](https://en.wikipedia.org/wiki/Stablecoin). Assuming that, on
average, USD stable coins are worth 1 USD, the bot is prepared to place a counter order
for any swap willing to trade `x` of token A for `y` of token B when `x < y`. It is
important to remember that execution fees must be factored into this decision-making
process so that the counter order placed should net a result of strictly more tokens
purchased than sold (including fees).

For this reason, the script is primarily intended to be run on xDai network where
transaction fees are negligible.



## LP Token Solver

**TODO** - design an HTTP solver which allow people to "swap"
[LP tokens](https://coinmarketcap.com/alexandria/glossary/liquidity-provider-tokens-lp-tokens)

In essence, the solver will fetch the open orderbook, filtering for orders whose buy or
sell token is an LP token. It will then encode the interactions necessary to enter or
exit liquidity from the corresponding pool.

### Advanced features

In the event that there is a
[coincidence of wants](https://en.wikipedia.org/wiki/Coincidence_of_wants)
(a.k.a. a *CoW*), the solver could match the orders directly to reduce the cost of
execution. Note that, A CoW in this scenario corresponds to a simultaneous desire to
provide and withdraw liquidity from a specific pool. 