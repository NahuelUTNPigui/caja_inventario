<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codProducto="0"
    let nombre="casa"
    let cantidad="15"
    let precio_venta = "100"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/productos')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/productos')
    }
</script>
detalle productos
<Container>
    <Row>
        <Col>
            <h2>Productos</h2>
            {#if codProducto == "0"}
                <p>Nuevo producto</p>
            {:else}
                <p>Modificar producto</p>
            {/if}
            <Form>
                <Container>
                    <Row>
                        <Col>
                            <Label for="nombre">Nombre</Label>
                            <Input
                              type="text"
                              name="nombre"
                              id="nombre"
                              placeholder="nombre"
                              bind:value="{nombre}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="cantidad">Cantidad</Label>
                            <Input
                              type="text"
                              name="cantidad"
                              id="cantidad"
                              placeholder="cantidad"
                              bind:value="{cantidad}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="precio_venta">Precio Venta</Label>
                            <Input
                              type="text"
                              name="precio_venta"
                              id="precio_venta"
                              placeholder="precio venta"
                              bind:value="{precio_venta}"
                            />
                        </Col>
                    </Row>
                    <Row>
                            
                        <Col>
                            <br>
                            <Button outline color="success" on:click={exito}>Guardar</Button>
                        </Col>
                        <Col>
                            <br>
                            <Button outline color="danger" on:click={cancelar}>cancelar</Button>
                        </Col>
                    </Row>
                </Container>
            </Form>
        </Col>
    </Row>
</Container>
