# bourbon-finder

Bourbon finder uses AWS Lambda as a web scraper to gather data once a week from the Iowa Highly Allocated Lottery website and sends the results to email.

https://abd.iowa.gov/alcohol/snapshot/lottery

Instructions

Option 1:
1. Manually deploy the IAM role, Lambda, SNS Topic, and EventBridge subscription.
   Example Resouces:

    - bourbon-finder-iam-role
    - bourbon-finder
    - bourbon-notification
    - bourbon-schedule
2. Create and add your AWS access key ID and secret into GitHub variables.
3. Enable GitHub Actions on your repo and use the deploy.yml file to update the lambda. 

Option 2:

Alternatively, you can use the provided CloudFormation template to deploy the AWS resources and Lambda code.

    - Be sure to make the appropriate changes for your account and region. 
1. Create a S3 bucket.
2. Create the deployment.zip file:
      - mkdir package
      - pip install --target ./package boto3
      - pip install --target ./package requests==2.31.0
      - pip install --target ./package bs4==0.0.1
      - cd package
      - zip -r ../deployment.zip .
      - cd ..
      - zip my_deployment_package.zip lambda_function.py
3. Upload deployment.zip to your S3 bucket. 
4. Run the cloudformation.yml with CloudFormation. 

Happy hunting :-)