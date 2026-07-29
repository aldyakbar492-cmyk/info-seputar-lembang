<!-- kalo maih eror jalankan ini di rules  -->

rules_version = '2';
service cloud.firestore {
match /databases/{database}/documents {

    function isAdmin() {
      return request.auth != null
        && request.auth.token.email == "sekitarlembang.web@gmail.com";
    }

    match /berita/{docId} {
      allow read: if true;
      allow write: if isAdmin();
    }

    match /videos/{docId} {
      allow read: if true;
      allow write: if isAdmin();
    }

}
}
