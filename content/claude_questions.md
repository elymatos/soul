## Questions for Clarification

1. **Frame Instantiation**: Should Frame instances maintain references to their parent Frame class, or operate independently once instantiated?
2. **Agent Communication Protocol**: How should we handle the message-passing between agents (methods) across different frames? Should this go through the Mind class or direct method calls?
3. **Persistence Strategy**: Which elements should persist in Neo4j versus remain in memory during processing? Should Frame definitions be persistent while instances are transient?
4. **Primitive Frame Bootstrap**: How do you envision initializing the base set of Image Schema and CSP primitive frames when the system starts?

- Frame Instantiation: I'm considering that once a frame is instantiated, it is independen of other frames. The connection with other frames will be done through the relations between frame elements.
- Agent Communication Protocol: I'm envisaging a direct communication between agents. The execution of an agent (this is, a method inside the object/frame) is programmatically defined.  When communicating, an agent must query Mind service to check if the destination frame is already instantiated and so send the message directly to it.
- Persistence Strategy: At first, frame definition will be kept in the code and Neo4j will be used to transient instances, during a processing phase.
- Bootstrap: when the system starts, just the Mind service will be started. This service is responsible to the communication with "external" world (for input/output) and for service some agents requests (for example, to query for instantiated frame or to instantiate a frame when necessary).


