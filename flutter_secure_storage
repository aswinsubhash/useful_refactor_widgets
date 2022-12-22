

//To persist login in a Flutter app with a splash screen using flutter_secure_storage and 
//GetX with a login controller, you can follow these steps:

// Step 1

class LoginController extends GetxController {
  final rxIsLoggedIn = false.obs;

  void setIsLoggedIn(bool value) {
    rxIsLoggedIn.value = value;
  }
}

// Step 2
//In the splash screen, retrieve the token ID from secure storage and 
//check if it is non-null. If it is, the user is logged in. If it is null, the user is not logged in
final storage = FlutterSecureStorage();
String token = await storage.read(key: 'token');
if (token != null) {
  // User is logged in
  Get.find<LoginController>().setIsLoggedIn(true);
} else {
  // User is not logged in
  Get.find<LoginController>().setIsLoggedIn(false);
}

//Step 3
//Based on the login state, navigate to the appropriate screen.
if (Get.find<LoginController>().rxIsLoggedIn.value) {
  // Navigate to the home screen
  Get.off(HomeScreen());
} else {
  // Navigate to the login screen
  Get.off(LoginScreen());
}

//Step 4
//When the user logs in successfully, store the token ID in secure storage and 
//update the login state in the controller. You can do this by using the write method of FlutterSecureStorage and 
//the setIsLoggedIn method of the controller:
final storage = FlutterSecureStorage();
await storage.write(key: 'token', value: tokenId);
Get.find<LoginController>().setIsLoggedIn(true);

//Step 5
//To log the user out, you can simply remove the token ID from secure storage and
// update the login state in the controller.
// You can do this by using the delete method of FlutterSecureStorage and the setIsLoggedIn method of the controller
final storage = FlutterSecureStorage();
await storage.delete(key: 'token');
Get.find<LoginController>().setIsLoggedIn(false);