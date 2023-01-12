<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codEgreso="0"
    let nombreProveedor="pedro"
    let fecha="12/11/2022"
    let monto = "100"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/egresos')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/egresos')
    }
</script>
<Container>
    <Row>
        <Col>
            <h2>Egreso</h2>
            {#if codEgreso == "0"}
                <p>Nuevo egreso</p>
            {:else}
                <p>Modificar egreso</p>
            {/if}
            <Form>
                <Container>
                    <Row>
                        <Col>
                            <Label for="proveedor">proveedor</Label>
                            <Input
                              type="text"
                              name="proveedor"
                              id="proveedor"
                              placeholder="proveedor"
                              bind:value="{nombreProveedor}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="monto">Monto</Label>
                            <Input
                              type="text"
                              name="monto"
                              id="monto"
                              placeholder="monto"
                              bind:value="{monto}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="fecha">Fecha</Label>
                            <Input
                              type="text"
                              name="fecha"
                              id="fecha"
                              placeholder="fecha"
                              bind:value="{fecha}"
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