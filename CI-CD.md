# Continuous Integration & Continuous Delivery/Development - CI / CD

# CI Workflow
- Multiple developers working on different bug fix or features
- Contribute to same application
- Sharing same code repository
- Frequently push updates into repo - at least daily
- Code change triggers automation build
- Need to ensure any code change does not break the build or introduce new bugs 
- Test framework runs automated tests on newly build application
- Identify bugs, preventing issues being introduced in the master code
- CI focus on small code changes which frequently committed into the main repo

# CD 

## Continuous Delivery
- A development practice
- Merged changes are automatically build, tested, and prepared for release into staging and eventually product environment
- These is usually a manual decision process to initiate deployment of the new code

## Continuous Deployment
- Automatically deploys new code following successful testing
- New code is automated release after passing stages

# CI/CD in AWS

- AWS Code Pipeline
    - AWS Code Commit
    - AWS Code Build 
    - AWS Code Deploy