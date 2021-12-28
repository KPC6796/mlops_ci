# mlops_ci
Comparison of ML models across two different Git branches of a project + automation using github actions

## Steps to follow:

python get_data.py --> data_raw.csv

python process_data.py --> data_processed.csv

python train.py

Create .gitignore file and put the data and image files

dvc init

dvc run -n get_data -d get_data.py -o data_raw.csv --no-exec python get_data.py --> dvc.yaml

-n --> name of the task
-d --> dependency (python callable)
-o --> output

Edit the dvc.yaml file as per the pipeline and output we desire.

dvc repro (execute the pipeline based on dvc.yaml file and recreate each stage)

git add .

git commit -m "setup dvc pipelines"

git push

## Setup github actions for CI

Create .github/workflows/train.yaml

Copy the template from cml github site

Add necessary parts in the run part of the train.yaml file

git add .

git commit -m "make CML workflow"

git push

Create another branch:
git checkout -b experiment_1

Make some changes in the train.py file:
ln3 and 31 changes are made.

git add .

git commit -m "trying QDA"

git push --set-upstream origin experiment_1




