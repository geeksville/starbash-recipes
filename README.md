# Starbash recipes

This is the default repo for starbash processing recipes.  See [starbash github](http://www.github.com/geeksville/starbash) for more information.

## Layout

Every recipe in this repo is one TOML file, listed in the `[[repo-ref]]` section of
[`starbash.toml`](starbash.toml) so Starbash can find it.

* `master/` - master (calibration frame) generation: `bias`, `dark`, `flat`
* `osc/` - one-shot-colour stacking (`stack_single_duo`, `stack_dual_duo`, ...) and per-frame registration reporting
* `palette/` - palette choices/recombinations (`broadband`, `hoo`, `sho`)
* `graxpert/` - background/gradient/noise elimination
* `rc-astro/` - BlurXTerminator / NoiseXTerminator
* `common/` - shared stages used by other recipes (`crop`, `starnet`, `thumbnail`)
* `post/` - finishing stages that run after stacking: `astro-color-stretch` (stretch) and `merge_stars` (blend the removed stars back)

Recipes are plain TOML + (optionally) a `python` script; some stages wrap engines
that live elsewhere - e.g. the VeraLux HyperMetric stretch comes from the
[`siril-scripts`](https://github.com/geeksville/siril-scripts) repo, and
`post/astro-color-stretch.toml` imports the GPL astro-color-stretch port that ships
inside Starbash (see `src/starbash/recipes/README.md` there).

## Credits

`post/astro-color-stretch.toml` wraps **astro-color-stretch** by [David M. Jones](https://dmjonesphotography.com/)
(GPL v3), an adaptation of Roger N. Clark's original rnc-color-stretch.  The
engine, its upstream copyright/licence header and the list of deliberate
deviations from the reference live in Starbash as
`src/starbash/recipes/astro_color_stretch.py`.

