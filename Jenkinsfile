properties([
  pipelineTriggers([
    [
      $class: 'BitBucketPPRTrigger',
      triggers : [
        [
          $class: 'BitBucketPPRPullRequestTriggerFilter',
          actionFilter: [
            $class: 'BitBucketPPRPullRequestCreatedActionFilter',
          ]
        ],
        [
          $class: 'BitBucketPPRPullRequestTriggerFilter',
          actionFilter: [
            $class: 'BitBucketPPRPullRequestApprovedActionFilter',
          ]
        ],
        [
          $class: 'BitBucketPPRPullRequestTriggerFilter',
          actionFilter: [
            $class: 'BitBucketPPRPullRequestUpdatedActionFilter',
          ]
        ],
        [
          $class: 'BitBucketPPRPullRequestTriggerFilter',
          actionFilter: [
            $class: 'BitBucketPPRPullRequestMergedActionFilter',
          ]
        ],
        [
          $class: 'BitBucketPPRRepositoryTriggerFilter',
          actionFilter: [
            $class: 'BitBucketPPRRepositoryPushActionFilter',
            triggerAlsoIfNothingChanged: true,
            triggerAlsoIfTagPush: false,
            allowedBranches: "",
            isToApprove: true
          ]
        ]
      ]
    ]
  ])
])

pipeline {
  agent any

  stages {
  stage('Build') {
      steps {
        echo 'Building...'

        echo 'Env vars for cloud pull request...'
        echo "BITBUCKET_SOURCE_BRANCH ${env.BITBUCKET_SOURCE_BRANCH}"
        echo "BITBUCKET_TARGET_BRANCH ${env.BITBUCKET_TARGET_BRANCH}"
        echo "BITBUCKET_PULL_REQUEST_LINK ${env.BITBUCKET_PULL_REQUEST_LINK}"
        echo "BITBUCKET_PULL_REQUEST_ID ${env.BITBUCKET_PULL_REQUEST_ID}"
        echo "BITBUCKET_PAYLOAD ${env.BITBUCKET_PAYLOAD}"

        echo 'Env vars for cloud push...'
        echo "REPOSITORY_LINK ${env.REPOSITORY_LINK}"
        echo "BITBUCKET_SOURCE_BRANCH ${env.BITBUCKET_SOURCE_BRANCH}"
        echo "BITBUCKET_REPOSITORY_URL ${env.BITBUCKET_REPOSITORY_URL}"
        echo "BITBUCKET_PUSH_REPOSITORY_UUID ${env.BITBUCKET_PUSH_REPOSITORY_UUID}"
        echo "BITBUCKET_PAYLOAD ${env.BITBUCKET_PAYLOAD}"

        echo 'Env vars for server push...'
        echo "REPOSITORY_LINK ${env.REPOSITORY_LINK}"
        echo "BITBUCKET_SOURCE_BRANCH ${env.BITBUCKET_SOURCE_BRANCH}"
        echo "BITBUCKET_REPOSITORY_URL ${env.BITBUCKET_REPOSITORY_URL}"
        echo "BITBUCKET_PUSH_REPOSITORY_UUID ${env.BITBUCKET_PUSH_REPOSITORY_UUID}"
        echo "BITBUCKET_PAYLOAD ${env.BITBUCKET_PAYLOAD}"
      }
    }
  }
}