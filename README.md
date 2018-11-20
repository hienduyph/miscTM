# Just Miscellaneous collections

## Mass delete github repos
- Generate a `delete_repo` token: https://github.com/settings/tokens/new
- Open your repos, e.g fork repos: https://github.com/hienduyph?utf8=%E2%9C%93&tab=repositories&q=&type=fork
Open JS console, run this code
```js
(() => {
	const repos = [];
    document.querySelectorAll('a[itemprop="name codeRepository"]').forEach(e => repos.push(e.getAttribute('href')))
    copy(repos);
})();
```

- Now create a script:
```bash
#! /usr/bin/env bash
# ./deleterepo.sh

repos=(
    # paste the repos from the clipboard and format its as bash shell array
)

for repo in "${repos[@]}"; do
    echo "deleting ${repo}"
    curl -X DELETE -H "Authorization: token <YOURTOKEN>" "https://api.github.com/repos$repo";
done
```

*Credits:*

- [Clean Up Unused GitHub Repositories!](https://medium.com/@xwildeyes/clean-up-unused-github-rpositories-c2549294ee45)^
