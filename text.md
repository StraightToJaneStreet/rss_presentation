The first thing we need in order to use WebGL for rendering is a canvas element on our page. 
Once we have the canvas, we try to get a WebGLRenderingContext for it by calling getContext() function and passing it the string 'webgl'.
After these manipulations, we get access to the opengl context for a concrete html canvas element.


Поговорить об отрисовке графики в браузере

Взаимодействие с видеокартой

OpenGL > OpenGL ES > ES = Embedded Systems

WebGL === OpenGL ES 2.0

OpenGL позволяет работать с драйвером видеокарты как с конечной машиной состояний, видеокарта работает независимо от пользовательского процесса а её состояние контролируется пользователем путем изменения некоторых параметров OpenGL

Шейдеры

1. Rendering Program
1.1 Rendering with OpenGL ES 2.0 requires the use of shaders, written in OpenGL ES's shading language, GLSL ES. Shaders must be loaded with a source string (shaderSource), compiled (compileShader) and attached to a program (attachShader) which must be linked (linkProgram) and then used (useProgram).


after this we can load a linked program to OpenGL and all thats left for us is set initial rendering data such as verticies and uniforms.

But actually not. Before wa can load our source data to graphics api we must have access to places into which this data can be loaded. 
In order to allow the shader program allocated in memory of our graphical card to access data from our ram memory we can use next api functions. First pair is gl.getAttribLocation and gl.enableVertexAttribArray.
  <section>
          <h1>WebGL</h1>
        </section>
        <section>
          <h3>Shaders compilation</h3>
          <pre><code class="language-cpp" data-trim data-line-numbers="1-11|1-2|4-5|7-8|10-11">
            const fShader = gl.createShader(gl.FRAGMENT_SHADER);
            const vShader = gl.createShader(gl.VERTEX_SHADER);

            gl.shaderSource(fShader, fSource);
            gl.shaderSource(vShader, vSource);

            gl.compileShader(fShader);
            gl.compileShader(vShader);

            gl.getShaderParameter(fShader, gl.COMPILE_STATUS);
            gl.getShaderParameter(vShader, gl.COMPILE_STATUS);
          </code></pre>
        </section>
        <section>
          <h3>Rendering program</h3>

          <pre><code class="language-cpp" data-trim data-line-numbers="1-10|1|3-4|6|8|10">
            program = gl.createProgram();

            gl.attachShader(shaderProgram, vertexShader);
            gl.attachShader(shaderProgram, fragmentShader);

            gl.linkProgram(shaderProgram);

            gl.getProgramParameter(program, gl.LINK_STATUS);

            gl.useProgram(program)
          </code></pre>
        </section>
        <section>
          <h3>Attributes/Uniforms locations</h3>
          <section>
            <p style="text-align: left">
              If we need to bind data from ram memory to memory allocated in graphical card we have must to know binding locations
              of the shader program.
            </p>
            <ul>
              <li>gl.getAttribLocation / gl.enableVertexAttribArray </li>
              <li>gl.getUniformLocation / gl.uniformMatrix </li>
            </ul>
          </section>
          <section>as</section>
        </section>
				<section>
          blabla
          <h2>Blabal</h2>
          <p>asdadd</p>
          <pre><code data-trim data-noescape>
            (def lazy-fib
              (concat
               [0 1]
               ((fn rfib [a b]
                    (lazy-cons (+ a b) (rfib b (+ a b)))) 0 1)))
            </code></pre>
            <p>adsasd</p>
        </section>
				<section>Slide 2</section>