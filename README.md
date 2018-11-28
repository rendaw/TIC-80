![TIC-80](https://tic.computer/img/logo64.png)
**TIC-80 TINY COMPUTER** - [https://tic.computer/](https://tic.computer/)
**Micromicro fork**

This is a fork that adds two new commands:

```lua
newcoin('yourgamename')
...
if pollcoin(bgcolor, fgcolor) then
	proceed()
end
```

that allow you to require and wait for a [micromicro](micromicro.cash) payment.

* `newcoin` prepares the payment.  This costs a small amount of money so you shouldn't call it every frame.

* `pollcoin` draws the QR code for the payment previously initialized with `newcoin` and returns `true` when the payment has been received.

The game name argument of `newcoin` needs to be added to [this list](https://gitlab.com/micromicro/games/blob/master/static/root/games.json) - create a PR if you'd like to include your game!

The new commands only work in html5 mode - when running outside of a browser `newcoin` does nothing and `pollcoin` always returns `true`.

# Building

Install emscripten and make sure your build directory is totally clean (no old build files).

Run:

```sh
emcmake cmake .
emmake make VERBOSE=1
```

The files `tic80pro.js` and `tic80pro.wasm` will be generated in `bin/`.  You can create an index page like [this one](https://tic.computer/embed) to run it in your browser.
