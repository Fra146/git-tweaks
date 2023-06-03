# Delete all actions from a repository
`user=GH_USERNAME repo=REPO_NAME; gh api repos/$user/$repo/actions/runs \
--paginate -q '.workflow_runs[] | select(.head_branch != "master") | "\(.id)"' | \
xargs -n1 -I % gh api repos/$user/$repo/actions/runs/% -X DELETE`
