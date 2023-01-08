<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button} from 'sveltestrap'
    import {ruta} from '../store'
    export let codClient="0"
    let nombre=""
    let apellido=""
    let telefono = ""
    let email = ""
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/clientes')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/clientes')
    }
</script>
detalle clientes
<Container>
    <Row>
        <Col>
            <h2>Clientes</h2>
            {#if codClient == "0"}
                <p>Nuevo cliente</p>
            {:else}
                <p>Modificar cliente</p>
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
                              placeholder="telefono"
                              bind:value="{telefono}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="email">Emial</Label>
                            <Input
                              type="text"
                              name="email"
                              id="email"
                              placeholder="email"
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
<style>

</style>