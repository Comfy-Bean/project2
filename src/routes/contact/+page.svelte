<script lang="ts">
  import { writable } from "svelte/store";
  import { validateForm } from "$lib/formValidator";

  type ErrorType = {
    name?: string;
    email?: string;
    phoneNumber?: string;
    address?: string;
  };

  let name = "";
  let email = "";
  let phoneNumber = "";
  let address = "";
  let reason = "";
  let additionalInfo = "";
  let errors = writable<ErrorType>({});

  function submitForm() {
    const validationErrors = validateForm(name, email, phoneNumber, address);
    console.log("Validation Errors:", validationErrors);
    if (Object.keys(validationErrors).length === 0) {
      console.log("Form Data:", {
        name,
        email,
        phoneNumber,
        address,
        reason,
        additionalInfo,
      });
      // Handle form submission
    } else {
      errors.set(validationErrors);
    }
  }
</script>

<section style="
 backdrop-filter: blur(50px);  font-family:'Crimson Text'; background-color: #E9A557; border-radius:10px;"
>
  <!-- HEADER -->
  <div class="relative">
    <img
      class="w-full h-[30vh] top-0 object-fit"
      src="assets/contact.jfif"
      alt=""
    />
    <div class="absolute inset-0 flex items-center justify-center">
     
    </div>
  </div>

  <!-- CONTENT -->
  <div class="container mx-auto py-10">
    <form
      on:submit|preventDefault={submitForm} 
      style="font-family:'Crimson Text'; background: white;
      border-shadow:(20px);
    text-align: center;
    font-size: 30px;
    color: white;} "
      class=" p-6 rounded-lg shadow-lg max-w-lg mx-auto"
    >
      <div class="mb-4">
        <label for="name" class="font-macondo text-black">Name:</label>
        <input
          type="text"
          id="name"
          bind:value={name}
          required
          class="w-full p-2 border rounded text-black"
        />
        {#if $errors.name}
          <p class="text-red-600">{$errors.name}</p>
        {/if}
      </div>
      <div class="mb-4">
        <label for="email" class="font-macondo text-black">E-mail:</label>
        <input
          type="email"
          id="email"
          bind:value={email}
          required
          class="w-full p-2 border rounded text-black"
        />
        {#if $errors.email}
          <p class="text-red-600">{$errors.email}</p>
        {/if}
      </div>
      <div class="mb-4">
        <label for="phoneNumber" class="font-macondo text-black"
          >Phone Number:</label
        >
        <input
          type="tel"
          id="phoneNumber"
          bind:value={phoneNumber}
          required
          class="w-full p-2 border rounded text-black"
        />
        {#if $errors.phoneNumber}
          <p class="text-red-600">{$errors.phoneNumber}</p>
        {/if}
      </div>
      <div class="mb-4">
        <label for="address" class="font-macondo text-black">Address:</label>
        <input
          type="text"
          id="address"
          bind:value={address}
          required
          class="w-full p-2 border rounded text-black"
        />
        {#if $errors.address}
          <p class="text-red-600">{$errors.address}</p>
        {/if}
      </div>
      <div class="mb-4">
        <label for="reason" class="font-macondo text-black"
          >Reason for Contact:</label
        >
        <input
          type="text"
          id="reason"
          bind:value={reason}
          class="w-full p-2 border rounded text-black"
        />
      </div>
      <div class="mb-4">
        <label for="additionalInfo" class="font-macondo text-black"
          >Additional Information:</label
        >
        <textarea
          id="additionalInfo"
          bind:value={additionalInfo}
          class="w-full p-2 border rounded text-black"
        ></textarea>
      </div>
      <button
        type="submit"
        class="bg-black text-white px-4 py-2 rounded-full hover:bg-green-500 transition duration-200"
        >Submit</button
      >
    </form>
  </div>
</section>

<style>
 
  
</style>
