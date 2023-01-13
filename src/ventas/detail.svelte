<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codVenta="0"
    let codCliente=""
    let nombreCliente="pedro"
    let fecha="12/11/2022"
    let monto = "100"
    let nombreProducto='papel'
    let cantidad="5"
    let precio_compra="1.5"
    let descripcion="soy una descripcion"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/ventas')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/ventas')
    }
    let detalles_compras=[
        {nombre_producto:'papel',cantidad:5,precio:1.0}
    ]
</script>
detalle ventas
<Container>
    <Row>
        <Col>
            <h2>Venta</h2>
            {#if codVenta == "0"}
                <p>Nueva venta</p>
            {:else}
                <p>Modificar venta</p>
            {/if}
            <Form>

                <Container>
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
                            <Label for="cliente">Cliente</Label>
                            <Input
                              type="text"
                              name="cliente"
                              id="cliente"
                              placeholder="cliente"
                              bind:value="{nombreCliente}"
                            />
                        </Col>
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
                            <Label for="nombreProducto">Producto</Label>
                            <Input
                              type="text"
                              name="nombreProducto"
                              id="nombreProducto"
                              placeholder="nombreProducto"
                              bind:value="{nombreProducto}"
                            />
                        </Col>
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
                        <Col>
                            <Label for="precio_compra">Precio compra</Label>
                            <Input
                              type="text"
                              name="precio_compra"
                              id="precio_compra"
                              placeholder="precio_compra"
                              bind:value="{precio_compra}"
                            />
                        </Col>
                        <Col>
                            <br>
                            <Button>Agregar o modifcar</Button>
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Table>
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Cantidad</th>
                                        <th>Precio</th>
                                        <th>Acciones</th>
                                        <th></th>
                                    </tr>
                                </thead>
                                <tbody>
                                    {#each detalles_compras as dc}
                                        <tr>
                                            <td>{dc.nombre_producto}</td>
                                            <td>{dc.cantidad}</td>
                                            <td>{dc.precios}</td>
                                            <td><Button>Modificar</Button></td>
                                            <td><Button>Eliminar</Button></td>
                                        </tr>
                                    {/each}
                                    <tr></tr>
                                </tbody>
                            </Table>
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="descripcion">Descripcion</Label>
                            <Input
                              type="text"
                              name="descripcion"
                              id="descripcion"
                              placeholder="descripcion"
                              bind:value="{descripcion}"
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