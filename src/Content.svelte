
<section class="grid">
    <div class="left">
        <h1>Mission</h1>
    </div>
    <div class="right">
        <section>
            <h2>Memorable</h2>
            <p>Brand values don't mean much if they're not constantly represented by the things you do and say. Your
                costumers and employees need to ble able to remember your beliefs if you want them to have an impact</p>
        </section>
        <section>
            <h2>Unique</h2>
            <p>This is something that should go without saying, but your brand values definition should be a unique reflection of your culture and identity. You can't simply copy and paste something that works for another business.</p>
        </section>
        <section>
            <h2>Actionable</h2>
            <p>Your brand value proposition is something that needs to guide how your business works, just like your brand manifesto. When defining what matters to your company, choose actionable language. For instance, don't just say you "value integrity"</p>
        </section>
        <section>
            <h2>Meaningful</h2>
            <p>Empty phrases that look as tough they've been picked at random from a dictionary won't do anything for your business. If you want your core brand values to resonate with your costumers, they need to include things your're willing to fight for.</p>
        </section>
        <section>
            <h2>Clear & Defined</h2>
            <p>Vague and value are two terms that rarely go together. When choosing the principles on which to build your brand, make sure that the things you stand for are easy to understand.</p>
        </section>
    </div>
</section>


<style>
 :root {
        --body-width: 1680px;
        --border-color: black;
        --border-type: solid;
        --border-width: 1px;
        --grid-row1: 30%;
        --grid-row2: 1fr;
        --color_second: #333;
        --color_third: blue;
        --text-size1: 2rem;
        --text-size2: 1.5rem;
        --text-size3: 1rem;
        --text-size4: 2rem;
		--text-color:#333;
		--text-color2:gray;
		--background: white;
    }
	
	html, body {
	position: relative;
	width: 100%;
	height: 100%;
	background: var(--background);
	color: var(--text-color);
}

body {
	margin: 0;
	/*padding: 8px;*/
	padding-left:2rem;
	padding-right:2rem;
	box-sizing: border-box;
	/*font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;*/
	font-family: -apple-system, BlinkMacSystemFont, sans-serif;
}

a {
	color: rgb(0,100,200);
	text-decoration: none;
}

a:hover {
	text-decoration: underline;
}

a:visited {
	color: rgb(0,80,160);
}

label {
	display: block;
}

input, button, select, textarea {
	font-family: inherit;
	font-size: inherit;
	-webkit-padding: 0.4em 0;
	padding: 0.4em;
	margin: 0 0 0.5em 0;
	box-sizing: border-box;
	border: 1px solid #ccc;
	border-radius: 2px;
}

input:disabled {
	color: #ccc;
}

button {
	color: #333;
	background-color: #f4f4f4;
	outline: none;
}

button:disabled {
	color: #999;
}

button:not(:disabled):active {
	background-color: #ddd;
}

button:focus {
	border-color: #666;
}
	
/*  */
	
	.grid {
        display: grid;
        grid-template-columns: var(--grid-row1) var(--grid-row2);
        border-bottom: var(--border-color) var(--border-type) var(--border-width);
        max-width: var(--body-width);
        margin: 0 auto;
		background: var(--background);
	color: var(--text-color);
    }

    section .grid {
        grid-template-columns: 100px 1fr;
    }

    .right {
        /*text-align: right;*/

        font-weight: bold;

    }

    .right section {
        display: grid;
        grid-template-columns: 35% 1fr;
        padding: 30px 20px 30px 40px;
        border-bottom: var(--border-color) var(--border-type) var(--border-width);
    }

    .right section p {
        font-weight: normal;
        font-size: 18px;
    }

    .right section h2 {
        font-weight: bold;
        font-size: 40px;
    }

    .right section:last-child {
        border: none;
    }

    .left {
        border-right: var(--border-color) var(--border-type) var(--border-width);
        padding-top: 30px;
        font-size: 40px;
        font-weight: bold;
				margin-left:40px;
    }

    h2 {
        font-weight: 800;
    }

    @media (max-width: 970px) {
			.right section {
                display: block;
                padding: 0;
            }
            .left{
                padding: 0;
                border-right: none;
                margin-left:0;
            }
            .right p{
                margin-bottom: 30px;
            }
            .grid{
                display: block;
            }
            .left{
                border-bottom: var(--border-color) var(--border-type) var(--border-width);
                border-right: none;
            }
	}
</style>