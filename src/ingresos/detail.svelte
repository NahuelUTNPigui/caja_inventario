<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codIngreso="0"
    let nombreCliente="pedro"
    let fecha="12/11/2022"
    let monto = "100"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/ingresos')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/ingresos')
    }
</script>
<Container>
    <Row>
        <Col>
            <h2>Ingreso</h2>
            {#if codIngreso == "0"}
                <p>Nuevo ingreso</p>
            {:else}
                <p>Modificar ingreso</p>
            {/if}
            <Form>
                <Container>
                    <Row>
                        <Col>
                            <Label for="cliente">Cleinte</Label>
                            <Input
                              type="text"
                              name="cliente"
                              id="cliente"
                              placeholder="cliente"
                              bind:value="{nombreCliente}"
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