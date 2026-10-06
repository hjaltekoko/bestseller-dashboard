# Brand Coverage Map

Static dashboard for Magasin bestseller coverage and price position. `data/` is updated every morning by the workflow in the private `bestseller_priceshape` repo; `index.html` is the page.

## Rolling back the products feature

Both repos carry the tag `v1-before-products`. To remove the feature:

```bash
# in bestseller_priceshape (private repo): stop writing the products tab and products.csv
git revert --no-edit v1-before-products..main && git push
# in bestseller-dashboard: restore the page without the products section
git checkout v1-before-products -- index.html && git commit -m "Remove products section" && git push
```

A softer switch: set the repository variable or secret `PRODUCTS_ENABLED=0` in the
workflow environment and the script skips the tab and the file; the page then shows
"Product list unavailable" in the drawer.
