# EKS-AB3

<img width="1479" height="703" alt="image" src="https://github.com/user-attachments/assets/6f09c4f4-8fc4-481b-90aa-a292308603fb" />

git add . && git committ -m "test CodeSuite" && git push origin master

Reference architecture

<img width="747" height="599" alt="image" src="https://github.com/user-attachments/assets/dd0facb4-c62c-4156-871b-622fdadbebf7" />
Figure 1 Workflow architecture showing source, build, test, approval and deployment stages

The code’s journey from the developer’s workstation to the final user-facing application is a seamless relay across various AWS services with key build an deploy operations performed via GitHub Actions:

1.The developer commits the application’s code to the Source Code Repository. In this post we will leverage a repository created in AWS CodeCommit.

2.The commit to the Source Control Management (SCM) system triggers the AWS CodePipeline, which is the orchestration service that manages the CI/CD pipeline.

3.AWS CodePipeline proceeds to the Build stage, where AWS CodeBuild, integrated with GitHub Actions, builds the container image from the committed code.

4.Once the container image is successfully built, AWS CodeBuild, with GitHub Actions, pushes the image to Amazon Elastic Container Registry (ECR) for storage and versioning.

5.An Approval Stage is included in the pipeline, which allows the developer to manually review and approve the build artifacts before they are deployed.

6.After receiving approval, AWS CodePipeline advances to the Deploy Stage, where GitHub Actions are used to run helm deployment commands.
Within this Deploy Stage, AWS CodeBuild uses GitHub Actions to install the Helm application on Amazon Elastic Kubernetes Service (EKS), leveraging Helm charts for deployment.

7.The deployed application is now running on Amazon EKS and is accessible via the automatically provisioned Application Load Balancer.
[
](https://aws.amazon.com/blogs/devops/simplify-amazon-eks-deployments-with-github-actions-and-aws-codebuild/)
