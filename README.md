COMPONENT (Widget, e.g., UserProfilePage)
   ↓ (calls method on Provider)
   ↓
SELECTOR (Consumer<UserProvider> or Provider.of<UserProvider>)
   ↑ (reads state from Provider)
   ↑
STORE (UserProvider, holds UserModel state)
   ↓ (dispatches action, e.g., updateUser)
   ↓
REDUCER (UserProvider method, e.g., _updateUserLocalState)
   ↔ (updates local state, notifyListeners)
   ↔
ACTION (UserProvider calls Service, e.g., userService.updateUser)
   ↓ (side effects, e.g., API call)
   ↓
EFFECTS (UserService, handles async API call)
   ↓ (interacts with Repository)
   ↓
SERVICE (UserRepository, makes GraphQL/REST call)
   ↓ (fetches/updates data)
   ↓
DATABASE / API (Backend, e.g., GraphQL endpoint or REST server)
   ↑ (response returned)
   ↑
SERVICE (UserRepository processes response)
   ↑
EFFECTS (UserService validates/ transforms data)
   ↑
ACTION (UserProvider receives data from Service)
   ↑
REDUCER (UserProvider updates state, notifyListeners)
   ↑
SELECTOR (Widget rebuilds with new state)
   ↑
COMPONENT (Widget reflects changes)
