---
title: rtAmazon S3
---

rtAmazon S3 allows site admin to move WordPress media uploads to Amazon S3 Bucket. This plugin works fine with [rtMedia](https://wordpress.org/plugins/buddypress-media/) plugin also.

## Installation
Perform the following steps to install rtAmazon s3 plugin:

  1. Download **rtAmazon S3** plugin from the [My Account](https://rtcamp.com/my-account) section
  
  2. Go to WordPress site dashboard and navigate to `Plugins > Add New > Upload`.
  
  3. Select the`rtamazon-s3.zip` file from your computer and click upload.
  
  4. Click **Install Now** to install the plugin. Then, click the **Activate Plugin** link, to activate the plugin.

## Settings

[![rtamazon-s3-login](https://cloud.githubusercontent.com/assets/7807348/8697331/b39a7d70-2b11-11e5-9ea7-160e5b6ebba6.png)](https://cloud.githubusercontent.com/assets/7807348/8697331/b39a7d70-2b11-11e5-9ea7-160e5b6ebba6.png)

1. You can define your `Access Key ID` and `Secret Access Key` in `wp-config.php` file. You can read more about wp-config options [here](#WPConfigOptions).

2. Enter `Amazon Access Kay ID`

3. Enter `Amazon Secret Access Key`

4. Click `Next` to get started

5. If you don't have an account then you can [Sign Up](https://console.aws.amazon.com/iam/home?region=us-east-1#users) to Amazon S3

6. Do not use your root credentials to login, it is best practice to use [IAM user](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAMBestPractices.html) and assign amazon s3 full access to the user,as this will protect your sensitive data.

## WP Config Options

You can directly add the settings right from your `wp-config.php` file. It will be more secure and only server team can do required changes. Site admin can't change any settings related to AWS S3 account and plugin settings. 

The following options are available for general use:

 - **Access Keys**
   
   Access keys consist of an **Access Key ID** and **Secret Access Key**, which are used to sign programmatic requests that you make to AWS. You can read more about it [here](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSGettingStartedGuide/AWSCredentials.html).
   
   Replace ***access_key_id*** and ***secret_access_key*** in the example code below with your ***Amazon Access Key ID*** and ***Amazon Secret Access Key*** respectively.
   
   ```define( 'RTAMAZON_S3_ACCESS_KEY_ID', 'access_key_id' );```
   ```define( 'RTAMAZON_S3_SECRET_ACCESS_KEY', 'secret_access_key' );```

 - **RTAMAZON_S3_BUCKET_NAME**

    To upload your data (photos, videos, documents etc.), you first create a bucket in one of the AWS regions. You can read rules for creating a bucket [here](http://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html).
    
    After creating a bucket replace ***bucket_name*** in the example code below with the ***Bucket*** you have just created or you want to access any.

    ```define( 'RTAMAZON_S3_BUCKET_NAME', 'bucket_name' );```

 - **RTAMAZON_S3_VIRTUAL_FOLDER_NAME**

    This option allows you to store your objects under folders on s3. For example if the name of your input folder is **test**, objects are stored under **test** folder, if folder name is **test/sample** objects are stored under **sample** folder which is a folder under **test** and so on.

    Replace ***virtual_folder*** in the example code below with the ***Folder*** you want.

    ```define( 'RTAMAZON_S3_VIRTUAL_FOLDER_NAME', 'virtual_folder' );```

 - **RTAMAZON_S3_DELETE_LOCAL_MEDIA**

    This option allows you to delete local server media after they have been successfully uploaded to your S3 account. You just need to set it **TRUE**. And if you don't want then you can remove this option or simply set it to **FALSE**. It is **Strongly Not Recommended** to delete local server media.

    For example use below code:

    ```define( 'RTAMAZON_S3_DELETE_LOCAL_MEDIA', 'TRUE' );```

 - **RTAMAZON_S3_FILE_URLS**

    There are four ways to serve media URL:

     1. **rtawss3_wp_url**: WordPress Media URL, i.e., `http://site.com/wp-content/uploads/2015/06/photo.jpg`.
     
         You can use below code:
         
         ```define( 'RTAMAZON_S3_FILE_URLS', 'rtawss3_wp_url' );```
     2. **rtawss3_subdomain**: Bucket Name as Subdomain, i.e., `http://bucket-name.s3.amazonaws.com/wp-content/uploads/2015/06/photo.jpg`.
     
         You can use below code:
         
         ```define( 'RTAMAZON_S3_FILE_URLS', 'rtawss3_subdomain' );```
     3. **rtawss3_path**: Bucket Name in Path, i.e., `http://s3.amazonaws.com/bucket-name/wp-content/uploads/2015/06/photo.jpg`.
     
         You can use below code:
         
         ```define( 'RTAMAZON_S3_FILE_URLS', 'rtawss3_path' );```
     4. **rtawss3_custom**: Custom Domain. This option is useful for CDN, CloudFront, etc.

        You can use below code:

        ```define( 'RTAMAZON_S3_FILE_URLS', 'rtawss3_custom' );```

        **Note:** If this option is set to **rtawss3_custom**, then **RTAMAZON_S3_CUSTOM_DOMAIN_NAME** option must be set. For example if you set 
        ```define( 'RTAMAZON_S3_CUSTOM_DOMAIN_NAME', 'example.com' );``` 
        then your media URL will become 
        ```http://example.com/wp-content/uploads/2015/06/photo.jpg.```

 - **RTAMAZON_S3_SYNC_UPLOAD**

    This option enables you to sync upload media files to S3 as they are uploaded from media library, blog post or rtMedia plugin. You just need to set it **TRUE**. And if you don't want then you can remove this option or simply set it to **FALSE**.

    ```define( 'RTAMAZON_S3_SYNC_UPLOAD', 'TRUE' );``` 

 - **RTAMAZON_S3_ALLOW_BUCKET_CREATION**

    This option allows you to give access for creating a bucket. If you want to allow to create a bucket, simply set it **TRUE**. And if you don't want then set it **FALSE** or remove this option.
    
    ```define( 'RTAMAZON_S3_ALLOW_BUCKET_CREATION', 'TRUE' );``` 

 - **RTAMAZON_S3_SHOW_ADMIN_SETTINGS_PAGE**

    This option is for showing **Settings** page. If set to **TRUE**, settings page will be displayed and if set to **FALSE**, settings page will not be displayed.

    ```define( 'RTAMAZON_S3_SHOW_ADMIN_SETTINGS_PAGE', 'TRUE' );```

 - **RTAMAZON_S3_SHOW_ADMIN_MENU**

    This option is for showing **Menus**. If set to **TRUE**, menus will be displayed and if set to **FALSE**, menus will not be displayed.

    ```define( 'RTAMAZON_S3_SHOW_ADMIN_MENU', 'TRUE' );```

 - **RTAMAZON_S3_BUCKET_REGION**

    This option is for setting bucket region. If your bucket is from **US Standard** region then you don't need to set this option. You can read more about region [here](http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region).

    For example if you want to set region as **US West (Oregon)** then use below code:

    ```define( 'RTAMAZON_S3_BUCKET_REGION', 'us-west-2' );```

## Bucket Selection

After successfully logged in, a dropdown will appear to select `Bucket selection` page.

[![rtamazon-s3-bucket-selection](https://cloud.githubusercontent.com/assets/7807348/8697527/3a26c6fe-2b13-11e5-9eee-ce6698885f27.png)](https://cloud.githubusercontent.com/assets/7807348/8697527/3a26c6fe-2b13-11e5-9eee-ce6698885f27.png)

1. You can see your `Access Key ID` and `Secret Access Key`

2. If you want to change your `Access Key ID` and `Secret Access Key` then enter new details and click on **Change** button

3. You can see you `Amazon S3 Buckets`.

4. If you want to add new bucket, click on `Create new Bucket` button

## Create Bucket

After clicking on `Create new Bucket`, you will be able to see `Bucket Creation Popup`

[![rtamazon-s3-create-bucket](https://cloud.githubusercontent.com/assets/7807348/8697591/f2f44c10-2b13-11e5-84bf-9c0ef7b9abba.png)](https://cloud.githubusercontent.com/assets/7807348/8697591/f2f44c10-2b13-11e5-84bf-9c0ef7b9abba.png)

1. Enter `Bucket Name`

2. Select `Region`

3. Click `Create Bucket` button.

4. You can see `Rules for creating Bucket`

5. If you don't want to create a Bucket then simply `Close` the popup.

## Bucket Settings

After `Selecting a Bucket` or `Creating a Bucket` you can see `Selected Bucket's` or `Created Bucket's` Settings.

[![rtamazon-s3-bucket-settings](https://cloud.githubusercontent.com/assets/7807348/8697753/1fd5fb42-2b15-11e5-9509-ae7aeba33e01.png)](https://cloud.githubusercontent.com/assets/7807348/8697753/1fd5fb42-2b15-11e5-9509-ae7aeba33e01.png)

1. Upload media files to **Virtual Folder** on Amazon S3 Bucket. For example if the name of input folder is **test**, media are stored under **test** folder, if folder name is `test/sample`, media are stored under **sample** folder which is a folder under **test** and so on.

2. You can delete local media files after they have been successfully uploaded to your **S3 Bucket**. If you enable this option then uploaded files are served with their `S3 URL`. **Strongly Not Recommended!**

3. You can serve media URL with different options:

    1. **WordPress Media URL**: `http://sp.com/wp-content/uploads/2015/06/photo.jpg`

    2. **Bucket Name as Subdomain**: `http://bucket-name.s3.amazonaws.com/wp-content/uploads/2015/06/photo.jpg`

    3. **Bucket Name in Path**: `http://s3.amazonaws.com/bucket-name/wp-content/uploads/2015/06/photo.jpg`

    4. **Custom Domain**: This option is useful for CDN, CloudFront, etc. For example if you enter **example.com** in the textbox, media URL will become `http://example.com/wp-content/uploads/2015/06/photo.jpg`

    **Note**: This will affect only new uploads.

4. You can directly copy uploaded media files to **S3 Bucket** as they are uploaded from media library, blog post or rtmedia plugin.

5. **Save Settings** after changes

6. You can see **Bucket Info** like:

    1. Bucket Name
  
    2. Bucket Owner
  
    3. Bucket Creation Date
  
    4. Bucket Versioning
  
    5. Bucket Location

7. You can **Delete Bucket** directly from here. If there are objects in the Bucket then you need to **Delete Objects** first.

8. You can see **Media Stats**

9. You can chnage the Bucket, if you want to see other Bucket details.

10. You can upload all the remaining media which are not uploded to Amazon S3 Bucket. Just click on **Upload All** button.

## Bucket Objects

[![rtamazon-s3-bucket-objects](https://cloud.githubusercontent.com/assets/7807348/8697809/d85d3ca2-2b15-11e5-9dda-ca5aefcbb550.png)](https://cloud.githubusercontent.com/assets/7807348/8697809/d85d3ca2-2b15-11e5-9dda-ca5aefcbb550.png)

1. If you want to list the latest bucket objects then click on **Refresh Bucket Object List**

2. Select Object

3. Bulk Actions

    1. `Download` -> You can download single object or multiple objects by selecting Download from Bulk Actions.
  
    2. `Delete` -> You can directly delete single object or multiple objects from the bucket by selecting Delete from Bulk Actions.
  
    3. `Move` -> First you have to select media and then select Move from Bulk Actions. After that select Destination Bucket.

4. Click `Apply` After select bulk action.

5. `Pagination` for bucket objects

## Upload All

You will be able to see **Remaining media count** which are not uploaded to Amazon S3 Bucket.

[![rtamazon-s3-upload-all](https://cloud.githubusercontent.com/assets/7807348/7202305/b4e26eb4-e52e-11e4-9d4f-f00ac468e69f.png)](https://cloud.githubusercontent.com/assets/7807348/7202305/b4e26eb4-e52e-11e4-9d4f-f00ac468e69f.png)

After Upload complete, click the link to navigate to **rtAmazon S3 Settings** as shown below

[![rtamazon-s3-upload-complete](https://cloud.githubusercontent.com/assets/7807348/7202390/6fbbca64-e52f-11e4-95b4-762ed61f47b9.png)](https://cloud.githubusercontent.com/assets/7807348/7202390/6fbbca64-e52f-11e4-95b4-762ed61f47b9.png)

### Upload Media
You can upload selected media to Amazon S3 Bucket.

[![rtamazon-s3-upload-media](https://cloud.githubusercontent.com/assets/7807348/8697857/452794c2-2b16-11e5-8aa8-0ae169c60b8b.png)](https://cloud.githubusercontent.com/assets/7807348/8697857/452794c2-2b16-11e5-8aa8-0ae169c60b8b.png)

1. Select the media you want to **Upload** to S3 Bucket

2. Click on **Upload**

## Media Library

You can upload media directly from WordPress' Media Library to **S3 Bucket** or see the uploaded media with their `S3 URL`

[![rtamazon-s3-media-library](https://cloud.githubusercontent.com/assets/7807348/7370914/f98fe2b2-edda-11e4-8ca1-b4af2faefa61.png)](https://cloud.githubusercontent.com/assets/7807348/7370914/f98fe2b2-edda-11e4-8ca1-b4af2faefa61.png)

1. You can see `Admin Notice` to upload remaining media to S3 Bucket.

2. New column to see/upload media i.e., `S3 URL`

3. `Upload` to S3 Bucket

4. `Link` to see the uploaded media

5. You can `Bulk Upload` by selecting multiple media and select `Upload to S3` from Bulk Actions DropDown.

## Reupload All

You can reupload all the media from your site to your amazon s3 account.

[![rtamazon-s3-reupload-all-media](https://cloud.githubusercontent.com/assets/7807348/8647856/4e26a444-2979-11e5-9937-5c74faa87de3.png)](https://cloud.githubusercontent.com/assets/7807348/8647856/4e26a444-2979-11e5-9937-5c74faa87de3.png)

After clicking on reupload link, you will be redirected to reupload all media page. On that page you just need to press **Start** button to start upload process.
