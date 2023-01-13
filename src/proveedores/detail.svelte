<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codProveedor="0"
    let nombre="pedro"
    let apellido="diaz"
    let telefono = "41242111"
    let email = "a@n"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/proveedores')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/proveedores')
    }
</script>
detalle proveedor
<Container>
    <Row>
        <Col>
            <h2>Proveedor</h2>
            {#if codProveedor == "0"}
                <p>Nuevo proveedor</p>
            {:else}
                <p>Modificar proveedor</p>
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
                            <Label for="apellido">Apellido</Label>
                            <Input
                              type="text"
                              name="apellido"
                              id="apellido"
                              placeholder="apellido"
                              bind:value="{apellido}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="telefono">Telefono</Label>
                            <Input
                              type="text"
                              name="telefono"
                              id="telefono"
                              placeholder="telefono venta"
                              bind:value="{telefono}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="email">Email</Label>
                            <Input
                              type="text"
                              name="email"
                              id="email"
                              placeholder="email venta"
                              bind:value="{email}"
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
