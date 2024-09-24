<script lang="ts">
  import { onMount } from "svelte";
  let users = [];
  onMount(async () => {
    const res = await fetch(`http://10.0.2.14:3000/user`);
    users = (await res.json()).data;
    console.log(users);
  });
</script>

{#each users as user, i (i)}
  {JSON.stringify(user)}
{/each}

<table>
  <thead>
    <th>STT</th>
    <th>Name</th>
    <th>UserName</th>
    <th>Email</th>
    <th>Active</th>
    <th></th>
  </thead>
  <tbody>
    {#each users as user, i (i)}
      <tr>
        <td>{i + 1}</td>
        <td>{user.full_name}</td>
        <td>{user.username}</td>
        <td>{user.email}</td>
        <td>{user.active}</td>
        <td><a href="/quanLyNguoiDung/{user.id}/sua">sua</a></td>
        
        
      </tr>
    {/each}
  </tbody>
</table>
