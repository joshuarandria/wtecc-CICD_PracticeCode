# Integrate Unit Test Automation

This folder holds the files for the lab: _Integrate Unit Test Automation_ which is part of the **IBM-CD0215EN-Skills Network Introduction to CI/CD** course.

kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml

tkn task ls

kubectl apply -f pvc.yaml

tkn hub install task flake8

kubectl apply -f pipeline.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog

kubectl apply -f tasks.yaml

kubectl apply -f pipeline.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog

tkn pipelinerun ls

tkn pipelinerun logs --last