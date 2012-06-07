var PATH = process.env["PATH"].split( ':' );
var MODULES_BIN = process.cwd() + "/node_modules/.bin";
PATH.unshift( MODULES_BIN );
PATH = PATH.join( ':' );

process.env["PATH"] = PATH;

var jake = require( "jake" );

desc( "start web server in project directory" );
task( "serve", [], function( port, base ) {
	var connect = require('connect');
    port = port || 8080;
  	base = base || process.cwd();

  	var middleware = [
    	connect.static( base ),
    	connect.directory( base )
  	];

  	connect.logger.format( "gladius", ("[D] server :method :url :status " +
    	":res[content-length] - :response-time ms" ));
  	middleware.unshift( connect.logger( "gladius" ) );

  	console.log( "starting web server on port " + port );
  	connect.apply( null, middleware ).listen( port );
});