# ENI tinted Kong

This is a mirrored repository of [Kong](https://github.com/Kong/kong). All branches and commits are automatically replicated by Gitlab. **Do not edit any branches beside mentioned ones.**

**NOTE** Always take care of the MTR_TARGET_TAG variable naming!

## How to edit/implement files?
We aim to implement and expand plugins to align with our requirements. To achieve this, we must establish a method for incorporating our modifications while retaining the capacity to integrate updates from Kong.

Consequently, we have adopted the following strategy: all modifications are exclusively carried out within branches prefixed with "eni-" under the "release/".

This implies that the "master" branch has an equivalent "eni-master" branch. Similarly, for each release, there exists a corresponding "eni-release/x.x.x.x" branch, which is eventually released as version "x.x.x.x". The last digit signifies the ENI-Version.

## How to build release?
1. Create a release branch named `eni-release/2.8.1.x` based on the `eni-release/2.8.1.x` branch.
2. If it's not configured in your preferred pipeline configuration file, prepare the release by setting MTR_TARGET_TAG to the appropriate image version
3. Update the ENI version within `kong/meta.lua`.
4. Tag the release using the name.
5. Initiate the image build by triggering the build job.
6. Once done, delete the `eni-release/2.8.1.x` branch.

## How to update our sources?
Release branches should not necessitate updates from the remote repository. On the other hand, "eni-master" can be kept up to date by merging changes from the "master" branch. This approach ensures that our modifications are retained while also staying current with updates.

**NOTE:** Starting from version 2.8.1 onwards, numerous merge conflicts have arisen from the "master" branch. Consequently, we will need to reapply our modifications to "eni-master" at a subsequent stage.

## How to built hotfixes?
There are two reasons for creating a hotfix:
1. In the event of a bug within our code, we can promptly address it by issuing a release such as "eni-2.8.1.x," even if this entails a departure from semantic versioning norms.
2. When it comes to rectifying bugs in Kong's releases, the procedure involves generating a new branch named "release/eni-2.8.x," utilizing the tag "eni-2.8.1" as the point of origin. Subsequently, the latest modifications are merged into this newly created branch.