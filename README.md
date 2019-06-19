# docs
Documents and guides for LunchBadger

# Installing
Clone the project with `git clone --recursive` parameter, so it will download all referenced submodules.

# Simple deploy
Building website is just calling `hugo` command from the folder
It will output `public folder` (or configure with `-d` flag)
Copy content of the public folder to `lunchbadger.github.io` repo

# options
`hugo --buildDrafts` will build drafts  (`-D`)
`--buildFuture` will include items that are set to appear in future (no need to shift clock) (`-F`)

# dev server
`hugo server -D -w --disableFastRender`open `localhost:1313` to view site
