# svg_img_download
in this rope shear how to download inline or embaded svg as image through javascript

### Alogrithm:

step1: add cdn in header section.

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.5.16/vue.js"></script>
<link type="text/css" rel="stylesheet" href="//unpkg.com/bootstrap/dist/css/bootstrap.min.css" />
```

step2: define id and xml link into your svg code.
```
<svg id="dynamicIllustration" version="1.1" width="320" height="480" viewBox="0 0 320 450" xmlns="http://www.w3.org/2000/svg">
        <rect x={{bedx}} y={{bedy}} width={{bedw}} height={{bedl}} style=" fill: none; stroke-width:1;stroke:rgb(0,0,0);" ></rect>
</svg>
```

step3: make a button or add event.

```
 <a  href="#" @click="downloadSVG($event)" class="link-download btn  btn-sm dropdown-item">Autocad</a>

```

step4 : define script code for download file.

```
<script>
Vue.config.devtools = false;
Vue.config.productionTip = false;

new Vue({
  el: '#app',
  data: {
    radius: 10
  },
  methods: {
    downloadSVG(evt) {

      // document.querySelector(".link-download").addEventListener("click", (evt) => {
      const svgContent = document.getElementById("dynamicIllustration").outerHTML,
        blob = new Blob([svgContent], {
          type: "image/svg+xml"
        }),
        url = window.URL.createObjectURL(blob),
        link = evt.target;

      link.target = "_blank";
      link.download = "layout.svg";
      link.href = url;
      // });

    }

  }

});
</script>

```

