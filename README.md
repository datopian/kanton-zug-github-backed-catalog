# A data catalog with data on GitHub

This example showcases a simple data catalog that get its data from a list of GitHub repos that serve as datasets.

A `datasets.json` file is used to specify which datasets are going to be part of the data catalog.

The application contains an index page, which lists all the datasets specified in the `datasets.json` file, and users can see more information about each dataset, such as the list of data files in it and the README, by clicking the "info" button on the list.

You can read more about it on the [Data catalog with data on GitHub](https://portaljs.org/docs/examples/github-backed-catalog) blog post.

## How to use

### Clone the repo

Clone this repo to get access to the code

```
git clone https://github.com/datopian/kanton-zug-github-backed-catalog 
cd kanton-zug-github-backed-catalog
```

### Set environment variables

This project uses the GitHub API, which for anonymous users will cap at 50 requests per hour, so you might want to get a [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) and add it to a `.env` file inside the folder like so

```
GITHUB_PAT=<github token>
```

### Change datasets

You can change the datasets that will be displayed in the data catalog by editing the file `datasets.json`. Some examples can be found inside [this repo](https://github.com/datasets).

### Run in development mode

Run the app using:

```
npm run dev
```

Open http://localhost:3000 from your browser. You should see something similar to this:

![](https://i.imgur.com/jAljJ9C.png)

If click on the `info` button for a dataset you will see a page similar to this:

![](https://i.imgur.com/AoJd4O0.png)

## Notes

### Structure of `datasets.json`

The `datasets.json` file is simply a list of datasets, below you can see a minimal example of a dataset:

```json
{
  "owner": "datopian",
  "branch": "main",
  "repo": "kanton-zug-github-backed-catalog",
  "files": [
    "datasets/sample-dataset/data_1.csv",
    "datasets/sample-dataset/data_2.csv"
  ],
  "readme": "datasets/sample-dataset/README.md"
},
```

It has:

- A `owner` which is going to be the github repo owner
- A `repo` which is going to be the github repo name
- A `branch` which is going to be the branch to which we need to get the files and the readme
- A list of `files` which is going to be a list of paths with files that you want to show to the world
- A `readme` which is going to be the path to your data description, it can also be a subpath eg: `example/README.md`

You can also add:

- A `description` which is useful if you have more than one dataset for each repo, if not provided we are just going to use the repo description
- A `Name` which is useful if you want to give your dataset a nice name, if not provided we are going to use the junction of the `owner` the `repo` + the path of the README, in the exaple above it will be `fivethirtyeight/data/nba-raptor`

### Extra commands

You can also build the project for production with:

```
npm run build
```

And run the production build with:

```
npm run start
```

## How to add more datasets 

### Developers

If you want to add a dataset you can just edit the `datasets.json` file and point to the dataset you want to add, in this example we have a few examples of that, in two of those we are pointing to this exact repo, more specifically to datasets inside the `datasets` folder.

Once you add those just commit your changes and they should appear automatically

### Non developers

This is a project that assumes some familiarity with github, if you are a non technical person you can still add a dataset, simply click on this icon right here in the repo page.
![](https://hackmd.io/_uploads/rkLaAxgD2.png)
And edit the `datasets.json` you can there point to the repo and path that you want to use

If you don't have a repo to point to, you can always just upload your data to this same repo, to do so we suggest you follow this [video](https://youtu.be/pgzOiH1kmnI?t=142) showing how to push data to github using a drag and drop ui, once you do this, just edit the `datasets.json` as described before.

