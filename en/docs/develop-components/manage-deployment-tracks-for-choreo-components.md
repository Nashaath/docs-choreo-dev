# Manage Deployment Tracks for Choreo Components

Choreo allows you to create and manage dedicated [deployment tracks](../choreo-concepts/deployment-tracks.md) for components, facilitating independent version control and deployment. This capability also allows you to unlink deployment tracks from associated branches or relink them to different branches so that you can align with your preferred Git workflows such as the feature branch workflow or GitFlow workflow.

!!! info
     Deployment track creation and management does not apply to API Proxy and [BYOI components](../develop-components/bring-your-own-image.md).


## Create a deployment track

**Prerequisites**:

 - A component created in Choreo.

Follow the steps below to create a deployment track for a component:

1. Sign in to the [Choreo Console](https://console.choreo.dev/).
2. In the **Component Listing** pane, click on the component for which you want to create a deployment track.
3. On the component overview page header, click the **Deployment Track** drop-down list.
4. Click **+ Create New**. This opens the **Create Deployment Track** dialog.
5. In the **Create Deployment Track** dialog, do the following:
    1. Select a branch to associate with the deployment track.
    2. Specify a description for the deployment track. This is optional.
    3. If you are creating the deployment track for a service component, specify a unique API version indicating the major and minor version numbers.
6. Click **Create**.

## Unlink a deployment track

If you want to detach a branch reference from a deployment track, you must unlink the branch.

!!! tip
     When you unlink an active deployment track, it doesn't stop ongoing deployments. However, it restricts future deployment actions to redeploy the same builds.


Follow the steps below to unlink a deployment track of a component:
  
1. Sign in to the [Choreo Console](https://console.choreo.dev/).
2. In the **Component Listing** pane, click on the component for which you want to unlink a deployment track.
3. On the component overview page header, click the **Deployment Track** drop-down list and then click **View All**. This takes you to the component settings page where you can see all the deployment tracks linked to the component.
4. Click the edit icon corresponding to the deployment track you want to unlink.
5. In the **Edit Branch** dialog that opens, click the **Branch Name** list and select **None**.
6. Click **Save**.

## Link a deployment track

To associate a branch reference to an unlinked deployment track, you must link a branch.

!!! tip
    When you link a branch that you have not used previously for an active deployment, it requires manual building and deployment for the associated deployment track.

**Prerequisites**:

 - A minimum of two branches in your GitHub repository.

Follow the steps below to link a branch to an unlinked deployment track:
  
1. Sign in to the [Choreo Console](https://console.choreo.dev/).
2. In the **Component Listing** pane, click on the component for which you want to associate a branch reference.
3. On the component overview page header, click the **Deployment Track** drop-down list and then click **View All**. This takes you to the component settings page where you can see all the deployment tracks linked to the component.
4. Click **+ Link Branch** corresponding to the unlinked deployment track for which you want to associate a branch.
5. In the **Link Branch** dialog that opens, click the **Branch Name** list and select the branch you want to relink.
6. Click **Save**.

## Relink a deployment track

To switch the branch reference of a linked deployment track, you must relink to an appropriate branch.

!!! tip
     Relinking a branch that was not previously used for an active deployment requires manual building and deployment for the associated deployment track.

**Prerequisites**:

 - A minimum of two branches in your GitHub repository.

Follow the steps below to switch the branch reference of a linked deployment track:
  
1. Sign in to the [Choreo Console](https://console.choreo.dev/).
2. In the **Component Listing** pane, click on the component for which you want to relink a deployment track.
3. On the component overview page header, click the **Deployment Track** drop-down list and then click **View All**. This takes you to the component settings page where you can see all the deployment tracks linked to the component.
4. Click the **Edit Branch** icon corresponding to the deployment track you want to relink.
5. In the **Edit Branch** dialog that opens, click the **Branch Name** list and select the branch you want to relink.
6. Click **Save**.

## Sample Scenario: Manage version releases with deployment tracks

Now, let’s take a look at a sample scenario to understand how a developer can use deployment tracks to manage version releases within Choreo:

Let’s consider the following version release scenario: 

- To initiate work on a new feature, a developer creates a new branch, named `feature-x` from either the `main` or `dev` branch.
- Once development is complete, the developer proceeds to merge the `feature-x` branch into the `dev` branch for testing.
- Upon successful testing in the `dev` branch, the developer proceeds to merge all the changes into the `main` branch for production deployment.

Following are the actions to take from a deployment tracks perspective in Choreo:

1. To prepare for the new version release, unlink the `main` branch from the associated deployment track (let’s consider this as deployment track 1).
2. Proceeds to merge the `dev` branch containing the tested changes into the `main` branch.
3. Unlink the dev branch from the associated deployment track (let’s consider this as deployment track 2).
4. Link deployment track 2 containing the latest version of the service to the `main` branch for deployment.
5. To facilitate ongoing development and testing, create another deployment track (let’s consider this as deployment track 3) and link it to the `dev` branch.

!!! tip
     - As a developer, you can strategically unlink and relink deployment tracks to effectively manage different versions of your services within Choreo.
     - You can create new deployment tracks for ongoing development branches like `dev` to ensure a continuous development and release cycle.