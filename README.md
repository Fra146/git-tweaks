# Delete all actions from a repository
`user=GH_USERNAME repo=REPO_NAME; gh api repos/$user/$repo/actions/runs \
--paginate -q '.workflow_runs[] | select(.head_branch != "master") | "\(.id)"' | \
xargs -n1 -I % gh api repos/$user/$repo/actions/runs/% -X DELETE`
# git yolo
`git config --global alias.yolo '!git add --all && git commit -m "$(curl -s https://whatthecommit.com/index.txt)" && git push`
then
`git yolo`
