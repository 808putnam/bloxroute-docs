# solana-trader-client-ts

Note, there is a .gitsubmodule file in the root folder. Use the following commands to pull in the solana-trader-proto repository as a submodule.

```bash
git submodule init
git submodule update
```

If you want to work on specific branch of solana-trader-proto:

1. `cd` inside the submodule directory.
2. `git checkout` the branch/commit you want to point to.
3. `cd` back to the main repository.
4. In `git status` you'll see that the submodule directory is modified.
5. In `git diff` you'll see the old and new commit pointers.When you `git commit` in the main repository, it will update the pointer.

**References**

1. [https://gist.github.com/gitaarik/8735255?permalink\_comment\_id=3130112#update-the-submodule-pointer-to-a-different-commit](https://gist.github.com/gitaarik/8735255?permalink\_comment\_id=3130112#update-the-submodule-pointer-to-a-different-commit)
2. [https://stackoverflow.com/questions/1777854/how-can-i-specify-a-branch-tag-when-adding-a-git-submodule](https://stackoverflow.com/questions/1777854/how-can-i-specify-a-branch-tag-when-adding-a-git-submodule)

Be sure to follow readme file - Development section to get necessary tooling in place.

`pbkit/pbkit` is used for proto builds. You can see how this works by examining package.json

```
npm run proto

# package.json
"proto": "pb-gen-ts --entry-path ./solana-trader-proto/proto --out-dir=./bxsolana/proto ./solana-trader-proto/proto/api.proto --ext-in-import=' '"
```

Install goland node.js plugin.

Setup a debug run for typescript from node.

TODO: Add example here.

Add environment variable to debug setup for API\_ENV set to local.

Optional environment variables: RUN\_LIFECYCLE, RUN\_STREAMS.

AUTH\_HEADER, PRIVATE\_KEY and PUBLIC\_KEY environment variables should be setup already from system environment variables.

References

1. [https://www.jetbrains.com/help/go/running-and-debugging-typescript.html#before\_you\_start](https://www.jetbrains.com/help/go/running-and-debugging-typescript.html#before\_you\_start)
