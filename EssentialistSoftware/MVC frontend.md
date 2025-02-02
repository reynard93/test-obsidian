arch patterns are blueprints for how to organise responsibilities
	- they separate responsibilities into **concerns**
The reality is _**getting to the first principles of this domain**_ isn’t really hard, it’s just that you need to become **extremely aware of all the various _doings_ and _knowings_ your** code is actually doing.

concerns are:: categories of responsibilities

example: Edit a User profile feature
```js
const UserProfile = () => {
  const [user, setUser] = useState({
    name: '',
    email: '',
    bio: ''
  });

  const handleChange = (event) => {
    setUser({
      ...user,
      [event.target.name]: event.target.value
    });
  };

  const handleSubmit = (event) => {
    event.preventDefault();

    axios
      .put('/api/profile', user)
      .then(response => {
        console.log('Profile updated successfully');
        // Handle success
      })
      .catch(error => {
        console.error('Error updating profile:', error);
        // Handle error
      });
  };

  return (
    <div>
      <h2>Edit Profile</h2>
      <form onSubmit={handleSubmit}>
        <label>
          Name:
          <input
            type="text"
            name="name"
            value={user.name}
            onChange={handleChange}
          />
        </label>
        <br />
        <label>
          Email:
          <input
            type="email"
            name="email"
            value={user.email}
            onChange={handleChange}
          />
        </label>
        <br />
        <label>
          Bio:
          <textarea
            name="bio"
            value={user.bio}
            onChange={handleChange}
          />
        </label>
        <br />
        <button type="submit">Save</button>
      </form>
    </div>
  );
};
```

Among the many responsibilities this code implements are the following:
![[Pasted image 20230813162024.png]]
concerns: (see how they are categories of logic?)
- state mgmt
- ui logic
- networking/api-logic

problem in the component: coupled concerns
The stuff that has to do with **state management** knows about the _**ui logic**_ stuff, which also knows about the _**networking & api logic**_ stuff.

There’s a lot of reasons why this is troublesome — the main one being that it kills our ability to test effectively — but at the code-first level, unless you’re aware of concerns, you’re not going to be able to separate them.

**Separate Concerns**
MVC gives us __three main concern-buckets__  
1. model
2. view
3. controller
![[Pasted image 20230813162403.png]]
- The **model** handles data and business logic
- The **view** handles the presentation
- The **controller** acts as the intermediary between the **model** and the **view**

refactoring: 
1. model: useUserModel hook, returns *state*
2. controller: UserController, contains handlers which calls api
3. view: UserView markup that takes the result of useUserModel (user) and UserController (handlers) via **props**
still have issues but good start

MVC is generic: applicable to backend, frontend, both

problem: doesn’t tell you how to structure what goes **within** those three main categories of responsibilities (concerns)
too broad strokes, there are more categories of responsibilities
![[Pasted image 20230813163145.png]]
