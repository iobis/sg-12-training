# Processing an eDNA dataset

## Authentication with GitHub

See the section on [Authentication](github.md#authentication) in the GitHub documentation.

## Forking the dataset repository

Go to the dataset repository at <https://github.com/iobis/sg-12-dataset> and clone the repository to your own GitHub account.

## Cloning the dataset repository

Open a new terminal in JupyterHub, navigate to the `work` folder, and clone your fork of the dataset repository. Make sure to change `<username>` in the command below to your own. After cloning, go into the dataset folder and create a new branch to work in.

```bash
git config --global core.sshCommand "ssh -i ~/work/id_rsa"
cd work
git clone git@github.com:<username>/sg-12-dataset.git
cd sg-12-dataset
git checkout -b develop
```

The dataset folder should now show up in the sidebar.

![](images/jupyter_clone.png)

## Creating a notebook

Close the terminal, navigate to `sg-12-dataset/scripts`, and create a new R notebook at `sg-12-dataset/scripts/<yourname>.ipynb`.

## Processing the dataset

An example solution is available at <https://github.com/pieterprovoost/sg-12-dataset/blob/develop/scripts/pieter.ipynb>. If necessary, download the notebook from GitHub and upload it to your scripts folder, or copy it from the scratch folder to your scripts folder.

### What to try

- Determine which core and extension tables you will need.
- Combine the ASV table, the taxonomy table, and the sample metadata into a Darwin Core occurrence table. Keep in kind that any ASV can occur in multiple samples.
- Use the `obistools` package for taxon matching. Optionally fix some of the non matching names manually.
- Use the `obistools` package for checking coordinates.
- Use the `obistools` package for checking dates.
- Use the `obistools` package to check for missing fields.
- Create an ExtendedMeasurementOrFact table. Possible measurements are sequence reads, sample size, and DNA concentration. Note that not all of these have terms in the NERC vocabulary server.
- Create a DNADerivedData table. Some of the information can be found in the metadata file.
- Write the individual tables to the `dwc/<yourname>` directory.
- To generate a Darwin Core Archive from Darwin Core data frames, you can use the <https://github.com/pieterprovoost/r-dwca-writer> package.

## Pushing your work to GitHub

![](images/jupyter_push.png)

```bash
(base) jovyan@82065e7c143d:~/work/sg-12-dataset$ git add .
```

```bash
(base) jovyan@82065e7c143d:~/work/sg-12-dataset$ git commit -m "example solution"
[develop 54b39e6] example solution
 1 file changed, 364 insertions(+)
 create mode 100644 scripts/pieter.ipynb
```

```bash
(base) jovyan@82065e7c143d:~/work/sg-12-dataset$ git push
fatal: The current branch develop has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin develop
```

```bash
(base) jovyan@82065e7c143d:~/work/sg-12-dataset$ git push --set-upstream origin develop
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 3.12 KiB | 319.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'develop' on GitHub by visiting:
remote:      https://github.com/pieterprovoost/sg-12-dataset/pull/new/develop
remote: 
To github.com:pieterprovoost/sg-12-dataset.git
 * [new branch]      develop -> develop
Branch 'develop' set up to track remote branch 'develop' from 'origin'.
```

## Checking your dataset using EMODnet BioCheck

Go to <https://rshiny.lifewatch.be/BioCheck/> and enter the URL of your Darwin Core Archive on GitHub. It should look like this: <https://github.com/pieterprovoost/sg-12-dataset/raw/develop/dwc/pieter/archive.zip>.