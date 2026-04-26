# LAB18_sec_android
en utilisant jadx-gui

<img width="1008" height="521" alt="image" src="https://github.com/user-attachments/assets/e693aa9b-9b99-431d-8191-aff4d2286ca8" />

Il existe une fonction Password qui récupère des chaînes depuis le fichier strings.xml et, parmi ces chaînes, une chaîne aléatoire est transmise à une fonction appelée generateRandomStrings. Cette fonction provient de la bibliothèque native firestorm.

La fonction Password n’est pas appelée, donc ce que nous devons faire, c’est utiliser Frida pour accrocher (hooker) cette fonction afin d’obtenir la valeur du mot de passe.
<img width="647" height="994" alt="image" src="https://github.com/user-attachments/assets/10370131-f8ed-4bb7-aa87-a0ed25650f2d" />

<img width="513" height="383" alt="image" src="https://github.com/user-attachments/assets/3bb360d3-b766-436c-90cf-50cc3866832f" />

<img width="954" height="335" alt="image" src="https://github.com/user-attachments/assets/4a27d996-2776-40be-bd6d-da032b835a2f" />

```
  Java.perform(function() {
      function getPassword() {
          Java.choose('com.pwnsec.firestorm.MainActivity', {
              onMatch: function(instance) {
                  console.log("MainActivity instance found: " + instance);
                  try {
                    var pass = instance.Password();
                    console.log("FireBase Password: " + pass);
                } catch (e) {
                    console.log("Error occurred: " + e);
                }
            },
            onComplete: function() {
                console.log("Search completed. Exiting script.");

            }
        });
    }

    setTimeout(getPassword, 4000);
});

```
FireBase Password: C7_dotpsC7t7f_._In_i.IdttpaofoaIIdIdnndIfC

