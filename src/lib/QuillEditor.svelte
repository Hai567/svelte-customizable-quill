<script>
    let { Quill, options = {}, data = "", class: class_attr } = $$restProps

    function init(node) {
        let off
        import("./quill.js").then(({ quill }) => {
            off = quill(Quill, node, data, {
                theme: "snow",
                ...options,
            })
        })
        return {
            destroy() {
                off && off()
            },
        }
    }
</script>

<div {...class_attr ? { class: class_attr } : {}}>
    <div use:init on:typing></div>
</div>
