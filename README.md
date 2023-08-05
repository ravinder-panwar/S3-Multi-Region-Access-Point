# S3-Multi-Region Access Point

Amazon S3 Multi-Region Access Points was a feature introduced by Amazon Web Services (AWS) to simplify the process of accessing data stored in Amazon S3 buckets across multiple regions. It allows you to create a single access point that abstracts away the complexity of dealing with multiple bucket locations and endpoints.

<h3>Overview</h3>

**Step 1:** Create S3 Buckets. <br>
**Step 2:** Create S3 Multi-Region Access Point.<br>
**Step 3:** Configure S3 Replication.<br>
**Step 4:** Failover Configuration.<br>
**Step 5:** IAM Permissions.<br>
**Step 6:** VPC Endpoints.<br>
**Step 7:** Monitor S3 Replication And Requests.<br>

<h3>Step 1: Create S3 Buckets.</h3>

1. Go to the **Amazon S3** console.

![1](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/97caa79b-1f96-41d5-bc82-3dc0ecbd70f2)

2. Create two buckets. Create these two buckets in two different regions. First **bucket** I created in **ap-south-1.**

![2](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/c8c5fad9-0f4d-4a75-b60b-cd93916dfba2)

![3](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/ebcddca2-442a-4a69-ac66-49f38e063bb2)

![4](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/211766cc-eba0-4db8-9ccc-e6f48749cad0)

3. Create another **bucket** but in **us-east-1** this time.

4. Once done creating both buckets, you will see both buckets.

![5](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/71cf50dc-2a04-46da-b3d2-0df6749ce5a4)

<h3>Step 2: Create S3 Multi-Region Access Point.</h3>

1.  Go to the **Amazon S3** console.
2.  Choose **Multi-Region Access Points**.
3.  **Create Multi-Region Access Point.**

![6](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/75257aea-c851-4bea-9214-87126fc889df)

4. Name it **my-new-mrap1.**
5. Add both buckets.
6. Block all public access.
7. Click on **Create Multi-Region Access Point.**

![7](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/ff30976f-a793-41f2-a6fc-f832ac5d7f6e)

![8](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/dacf9858-a94b-4672-acd8-972c8424173a)

8. Wait for its status to show as **Ready** before proceeding.

![9](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/4b95071c-cc77-4180-9de0-da6b7595108a)

<h3>Step 3: Configure S3 Replication.</h3>

1. Select the name of your Multi-Region Access Point to configure additional settings.
2. Go to **properties** and copy-paste the **ARN** to the notepad as you will be needing it later.

![10](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/99e6aa71-6588-40b3-881b-f032eb532416)

3. Select the **Replication and Failover** tab.

![image](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/49b1643f-db3a-40e6-a28c-cdc791a78b79)

4. Scroll down a little, and click on **Replication rules**.
5. **Create replication rules.**

![11](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/12e29734-8fbe-44c5-9373-3edb46f17626)

6. **Choose template.**
7. Choose the **Replicate objects among all specified buckets** template.

![12](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/28e978a1-3e81-478d-a9a7-8755c434f40f)

8. Add buckets and **Enable bucket versioning.**

![13](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/c34b6ca9-04db-47e6-9e19-b4a1a9ef5f6d)

9. For **Scope**, choose **Apply to all objects in the bucket.**

![14](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/0b465e18-af9a-4639-9525-257aa378349f)

10. In **Additional replication options**, configure the following, and click on **Create replication rules.**

![15](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/ac63acd6-b131-449a-aae7-316c61ac67ef)

11. Go to the **Amazon S3** console.
12. Select any bucket (I chose **bucket1-in-mumbai**).
13. Upload any object in it.

![16](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/c533e754-16fb-4453-9fe6-95cde87d8f5a)

![17](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/e00785f9-4a2a-4741-b4ae-77e553cb3b8c)

<h3>Step 4: Failover Configuration.</h3>

1. Open the **Replication and failover** tab of your new Multi-Region Access Point.
2. Go to **Failover configuration.**
3. Select any one bucket.
4. Then, click on **Edit routing status.**

![18](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/c4a5ff25-9dd8-4f98-ae45-33d8abce4e73)

5. Click on **Passive** and **save routing status.**

![19](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/645d82e9-6f7b-44fa-b7d1-894a1039356f)

6. Once done, now select both buckets and click on **Failover.**
7. Click on **Failover.**

![20](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/8e313b5b-2501-47b7-be28-a09948f92459)

![21](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/1b1e00ff-baf4-4891-94f0-deaa7c60df64)

<h3>Step 5: IAM Permissions.</h3>

1. Go to the **AWS Console** and copy the **Account Id.** and paste it on the notepad.

![22](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/e1df9637-0982-4a69-a47c-934d0c8e30f7)

2. Go to the **S3**, select a **bucket**, click on **properties**, and copy-paste the ARN in **Notepad.**

![23](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/a83e546c-f0e4-4ad5-9dac-da6d44f9328c)

3. Go to **Bucket policy**.
4. Click on **Edit bucket policy** and select **json**.
5. Configure the policy and **save.**

![24](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/c66ffde3-041c-4906-8287-160e909d7b02)

6. **Repeat. Make sure to do the same with the other bucket also.**

<h3>Step 6: VPC Endpoints.</h3>

1. Go to **VPC.**
2. On the left navigation pane, select **Endpoints.**
3. Click on **Create endpoint.**

![25](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/4300c83c-82fb-4dd1-9972-537a97d3ef63)

4. Name it.
5.Choose **AWS Services** in service category.

![26](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/08817f1f-9c53-4413-bcf7-5670113e318b)

6. In the **Services** section, in the Filter services search bar, enter **S3**. Then, choose **com.amazonaws.s3-global.accesspoint.**

![27](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/2d5a0a23-4cb1-448b-a845-30e816ba3fb3)

7. Select the **subnets**, add **security groups**, and you're almost done.

![28](https://github.com/ravinder-panwar/S3-Multi-Region-Access-Point/assets/133412857/146751c1-4ef1-42ba-a9a6-a83afc5aae18)

<h3>Step 7: Monitor S3 Replication and Requests</h3>

1. Generate some test traffic.
2. Monitor it in **Cloudwatch**.

<h2> Congratulations! Project Completed.</h2>





























