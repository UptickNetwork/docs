# Upgrade Genesis File

{% hint style="info" %}
If the new version you are upgrading to has breaking changes, you will have to [export](https://docs.uptick.network/guides/upgrades/upgrade\_node.html#export-state) the state and [restart](https://docs.uptick.network/guides/upgrades/upgrade\_node.html#restart-node) your node.

If it is **not** breaking (eg. from `v0.1.x` to `v0.1.<x+1>`), you can skip to [Restart](https://docs.uptick.network/guides/upgrades/upgrade\_node.html#restart-node) after installing the new version.
{% endhint %}

To upgrade the genesis file, you can either fetch it from a trusted source or export it locally using the `uptickd export` command.
