# Let yarn resolve git conflicts

When resolving git conflicts having a javascript project `yarn` can be used to resolve conflicts in `yarn.lock`.

I've had a case where I only resolved the conflicts in `package.json`.
Then I just called `yarn` which gave me this output:

```shell
> yarn
yarn install v1.22.4
info Merge conflict detected in yarn.lock and successfully merged.
```

No source. Just saw it when I tried to yarn after only resolving `package.json`.
