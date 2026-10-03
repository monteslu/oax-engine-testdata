# oax-engine-testdata

Reference images and traces for the test suite of the
[oax engine](https://github.com/monteslu/oax-engine). They live here, not in
the engine repo, so that people who only build and play get a small clone.

You need this repo only to run the engine's romdev tests
(`tests/romdev/run.mjs`, `misc/ci/gate.sh`). Clone it next to the engine:

    git clone https://github.com/monteslu/oax-engine.git
    git clone https://github.com/monteslu/oax-engine-testdata.git

or point the tests at it with `OAX_TESTDATA=/path/to/oax-engine-testdata`.
The tests refuse to run without it rather than writing new references.

## Layout

| Path | What | Written by |
| --- | --- | --- |
| `goldens/stock/` | stock OpenArena maps, two views each, cart renderer | `stock-maps --update` |
| `goldens/render/` | render goldens, three stock maps | `render-goldens --update` |
| `goldens/oax/`, `goldens/surfworld/`, `goldens/terrain/`, `goldens/gui/` | oax feature tests on the engine's own test maps | the matching test with `--update` |
| `goldens/movement/` | movement traces (JSON) | `movement-traces --update` |
| `reference/native/` | the native desktop renderer from the same cameras, the look the cart is held to | `tests/romdev/reference/capture-native.mjs` |
| `reference/ulight/` | native renders for the unified-lighting goldens | `ulight-goldens --update` |

Goldens are stored at half size (a 2x2 box filter of the captured frame).

## Updating

Regenerate only for a change you can explain: a golden that moved for an
unexplained reason is a bug report, not a golden to replace. Commit the new
images here and name the engine commit that changed them in the message.

## Licence

The images are renders of OpenArena content (GPLv2) and of the engine's
own test maps, made with the oax engine (GPL). They are distributed under the
GNU General Public License, version 2 or (at your option) any later version.
