<script>
  let user = {};

  async function handleSave() {
    let res = await fetch("http://10.0.2.14:3000/user", {
      method: "POST",
      body: JSON.stringify(user),
      headers: { "Content-Type": "application/json" },
    });
  }
  if (res == 201) {
    goto("/quanLyNguoiDung");
  } else {
    alert("Error");
  }
  console.log(res);
</script>

{JSON.stringify(user)}

<form action="" on:submit={handleSave}>
  <label for="full-name">Ho va ten</label>
  <input type="text" name="" id="" bind:value={user.full_name} />

  <label for="username">ten dang nhap</label>
  <input type="text" name="" id="" bind:value={user.username} />
  <label for="email">email</label>
  <input type="email" name="" id="" bind:value={user.email} />
  <label for="password">mat khau</label>
  <input type="password" name="" id="" bind:value={user.password} />
  
  <button type="submit">Save</button>

</form>
