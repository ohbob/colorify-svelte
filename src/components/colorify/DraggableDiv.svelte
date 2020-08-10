<style>
    .DraggableDiv {
        position: fixed;
        max-width: 300px;
        border: 1px solid #aaa;
        border-radius: 2px;
        box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
        padding: 1em;
        margin: 0 0 1em 0;
        background: white;
    }

</style>

<div class="DraggableDiv"
     use:pannable
     on:panstart={handlePanStart}
     on:panmove={handlePanMove}
     on:panend={handlePanEnd}
     style="transform:
		translate({$coords.x}px,{$coords.y}px)
		">
    <slot></slot>
</div>


<script>
    import {spring} from 'svelte/motion';
    import {pannable} from './pannable.js';

    const coords = spring({x: 0, y: 0}, {
        stiffness: 0.2,
        damping: 0.4
    });

    function handlePanStart() {
        coords.stiffness = coords.damping = 1;
    }

    function handlePanMove(event) {
        coords.update($coords => ({
            x: $coords.x + event.detail.dx,
            y: $coords.y + event.detail.dy
        }));
    }

    function handlePanEnd(event) {
// 		coords.stiffness = 0.2;
// 		coords.damping = 0.4;
// 		coords.set({ x: 0, y: 0 });
    }
</script>