FINAL PROJECT- TAXI MOTO APP

TaxiMotoApp: is an Android application that lets you register motorcycle taxi drivers and manage basic task elements, including adding new users.

Submitted by: ZIDOR Jean Rousso

Time spent: 6 hours spent in total
 
User Stories

[] User can successfully Login from the OAVCT 

[] User can download the app on playstore

[] User can Enregister

[] User can browse a drive to get a ride

[] User can request for address, phone, email change on the app

 [] user can add money in his wallet  
 
 
GIF created with LiceCap.

Steps to integrate automatic connection with google account
Intégration de la connexion Google dans votre application Android
Ajoutez le bouton de connexion Google à votre application Le bouton de connexion Google standardAjoutez le SignInButton dans la mise en page de votre application:
<com.google.android.gms.common.SignInButton android:id="@+id/sign_in_button" android:layout_width="wrap_content" android:layout_height="wrap_content" />
Facultatif : si vous utilisez le graphique du bouton de connexion par défaut au lieu de fournir vos propres ressources de bouton de connexion, vous pouvez personnaliser la taille du bouton avec la setSize méthode.
// Définissez les dimensions du bouton de connexion. SignInButton signInButton = findViewById ( R . Id . Sign_in_button ); signInButton . setSize ( SignInButton . SIZE_STANDARD ); Dans l'activité Android (par exemple, dans la onCreateméthode), enregistrez vos boutons OnClickListenerpour vous connecter à l'utilisateur lorsque vous cliquez dessus:
findViewById(R.id.sign_in_button).setOnClickListener(this); ##Démarrer le flux de connexion Dans la onClickméthode de l'activité , gérez les pressions sur les boutons de connexion en créant une intention de connexion avec la getSignInIntent méthode et en commençant l'intention avec startActivityForResult.
@Override public void onClick(View v) { switch (v.getId()) { case R.id.sign_in_button: signIn(); break; // ... } }
signe vide priv é () {
Intention signInIntent = mGoogleSignInClient . getSignInIntent (); startActivityForResult ( signInIntent , RC_SIGN_IN ); }
Le démarrage de l'intention invite l'utilisateur à sélectionner un compte Google avec lequel se connecter. Si vous avez demandé des étendues au profile- delà de , emailet openid, l'utilisateur est également invité à accorder l'accès aux ressources demandées.
Une fois l'utilisateur connecté, vous pouvez obtenir un GoogleSignInAccount objet pour l'utilisateur dans la onActivityResultméthode de l'activité .
@Passer outre public void onActivityResult ( int requestCode , int resultCode , Intent data ) {
super . onActivityResult ( requestCode , resultCode , données );
// Résultat renvoyé par le lancement de l'intention depuis GoogleSignInClient.getSignInIntent (...);
si ( requestCode == RC_SIGN_IN ) {  
    // La tâche renvoyée par cet appel est toujours terminée, pas besoin de l'attacher
    // un auditeur.
    Tâche < GoogleSignInAccount > task = GoogleSignIn . getSignedInAccountFromIntent ( données ); 
    handleSignInResult ( tâche );
}
 
}
private void handleSignInResult ( Task < GoogleSignInAccount > doneTask ) {
essayez { Compte GoogleSignInAccount = completeTask . getResult ( classe ApiException . );
   // Connecté avec succès, afficher l'interface utilisateur authentifiée.
    updateUI ( compte );
} catch ( ApiException e ) {   
    // Le code d'état ApiException indique la raison détaillée de l'échec.
    // Veuillez vous référer à la référence de la classe GoogleSignInStatusCodes pour plus d'informations.
    Connectez-vous . w ( TAG , "signInResult: code échoué =" + e . getStatusCode ());  
    updateUI ( null );
}
 
}
License

Copyright [yyyy] [ZIDOR Jean Rousso]
 
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
 
    http://www.apache.org/licenses/LICENSE-2.0
 
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
 
App TAXI MOTO

TaxiMoto
 

