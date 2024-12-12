![ecommerce-app2](https://github.com/user-attachments/assets/7ab1b795-44ae-483f-aa85-71c23de56d8a)

# Build a Full E-commerce Application with Admin Control in Flutter with Firebase, Stripe

_don't just copy and paste the code from here try to learn from it, it will be more beneficial for you._

### [Checkout the full tutorial here](https://youtu.be/SsKNRwYPlrw)

⚠️ Important :

- Updated the code swap the functions firebase storage with cloudinary for image storage in `ecommerce_admin_app`.
- ### Changes you need to do :

  - add packages `http`,`flutter_dotenv` using

  ```bash
    flutter pub add http flutter_dotenv
  ```

  - create .env at the root of `ecommerce_admin_app`

  ```bash
    CLOUDINARY_CLOUD_NAME="*******"
    CLOUDINARY_API_KEY="**************"
    CLOUDINARY_SECRET_KEY="*************"
  ```

  - add .env to assets in pubspec.yaml

  ```bash
    assets:
    - .env
  ```

  - main function modify

  ```dart
  void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
  await dotenv.load(fileName: ".env");
  runApp(const MyApp());
  }
  ```

  - copy the contents of `lib/controllers/cloudinary_service.dart`

  - modify the image upload function user this instead of the old one, for `ModifyCategory()` in `categories_page.dart`,`ModifyProduct()` in `modify_product.dart`,`ModifyPromo()` in `modify_promo.dart`

  ```dart
   void _pickImageAndCloudinaryUpload() async {
    image = await picker.pickImage(source: ImageSource.gallery);
    if (image != null) {
      String? res = await uploadToCloudinary(image);
      setState(() {
        if (res != null) {
          imageController.text = res;
          print("set image url ${res} : ${imageController.text}");
          ScaffoldMessenger.of(context).showSnackBar(
              const SnackBar(content: Text("Image uploaded successfully")));
        }
      });
    }
  }
  ```

### What You'll Learn:

- Firebase Authentication & Firestore Integration
- Implementing Sign-up, Login, and Password Reset
- Real-time Database with Cloud Firestore
- CRUD Operations for Categories, Products, Promos, and Coupons
- Image Uploads to Firebase Storage
- Stripe Payment Gateway Setup
- Building Dynamic UI for Admin and Client Apps
- Creating and Managing Shopping Cart and Orders
- Handling Discounts, Coupons, and Promo Codes
- Secure Checkout Flow and Order Receipts
- Optimizing State Management with Providers
- Managing Streams in Flutter for Real-Time Updates

## Authors:

- [Snehasis4321](https://github.com/Snehasis4321)
