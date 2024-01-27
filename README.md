# todolist

### 1- Refs
like Dom-js querySelector
```php
<div ref="refName">Content</div>
this.$refs.refName.style.color = "red";
```

### 2- Props
to pass data from parent to child components
```php
in app => <Modal :header="header variable" theme="dark"/>
in Modal component => 
export default{
    props: ['header', 'theme']
}
then you can use it => {{header}}
& can create class if condition true => <div class="modal" :class="{dark_color: theme === 'dark'}"></div>
```

### 3- Emitting custom events
```php
in app => 
<div v-if="showModal">
    <Modal/>
</div>
<button @click="toggleModal">show modal</button>
& in data => showModal:false
& in methods => 
toggleModal(){
      this.showModal = !this.showModal
},
```

### 4- fire function
```php
in modal component => 
<div class="backdrop" @click ="closeModal">
    <div class="modal">..</div>
</div>
in methods => 
closeModal(){
    this.$emit('close');
}

in app => 
<Modal :header="header" theme="dark" @close="toggleModal"/>
in methods => 
toggleModal(){
    this.showModal = !this.showModal
},
```

### 5- Click event modifier
```php
<div @click.self ="closeModal">..</div>
@click.self or @click.right ....
```

### 6- Slots
```php
in app => 
<Modal :header="header" theme="dark" @close="toggleModal">
    <template v-slot:links>
        <a href="">link 1</a>
    </template>
    <h1>{{title}}</h1>
</Modal>
in Modal component => 
<div class="modal">
    <h1>text from modal</h1>
    <slot></slot> => will show all inside modal tag exept template with name of slot
    <div class="actions">
        <slot name="links"></slot> => will show template that has name of slot 
    </div>
</div>
```

### 7- Teleport
-- inside index.html => <div id="app"></div> <br>
and if we want make <div id="modals"></div> => and show modals inside this not inside app id => <br>
name tag (teleport) and (to="#modals")

```php
<teleport to="#modals" v-if="showModal">
    <Modal :header="header" theme="dark" @close="toggleModal">
      <template v-slot:links>
        <a href="">link 1</a>
      </template>
      <h1>{{title}}</h1>
    </Modal>
</teleport>
```

