<script>
  function encode(data) {
    return Object.keys(data)
      .map(
        (key) => encodeURIComponent(key) + "=" + encodeURIComponent(data[key])
      )
      .join("&");
  }

  function handleSubmit(event) {
    event.preventDefault();
    fetch("/", {
      method: "POST",
      headers: { "Content-Type": "application/x-www-form-urlencoded" },
      body: encode({
        "form-name": event.target.getAttribute("name"),
        ...name,
      }),
    }).catch((error) => alert(error));
  }
</script>

<form
  data-netlify="true"
  name="pizzaOrder"
  method="post"
  on:submit={handleSubmit}>
  <label>What order did the pizza give to the pineapple?
    <input name="order" type="text" />
  </label>
  <input type="submit" />
</form>
