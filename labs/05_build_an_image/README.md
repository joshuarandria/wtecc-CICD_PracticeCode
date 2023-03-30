# Building an Image

This folder holds the files for the lab: _Building an Image_ which is part of the **IBM-CD0215EN-Skills Network Introduction to CI/CD** course.

kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml

tkn hub install task flake8
kubectl apply -f tasks.yaml
tkn clustertask ls
kubectl apply -f pipeline.yaml
kubectl apply -f pvc.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch=main \
    -p build-image=image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/tekton-lab:latest \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog

tkn pipelinerun ls

tkn pipelinerun logs --last