# Lazy loader project

Basic structure of an angular project with single page application and lazy loading.

## Struture:

  - AppModeule
    - Header
    - Home
      - FistPage
    - Footer
 
 # Resume

	AppModule - import BrowserModule
	AppRoutingModule
		{
		    path: '',
		    loadChildren: () => import('./pages/home/home.module').then(m => m.HomeModule)
		 }	
	FirstPageModule - import CommonModule	
	FirstPageRoutingModule - RouterModule
		{ path: '', component: FirstPageComponent }



# Implementation

# AppModule - BrowserModule
----------------------------------------------------------------
	import { NgModule } from '@angular/core';
	import { BrowserModule } from '@angular/platform-browser';
	import { AppRoutingModule } from './app-routing.module';
	import { AppComponent } from './app.component';
	import { HeaderComponent } from './header/header.component';
	import { FooterComponent } from './footer/footer.component';

	@NgModule({
	  declarations: [
	    AppComponent,
	    HeaderComponent,
	    FooterComponent
	  ],
	  imports: [
	    BrowserModule,
	    AppRoutingModule
	  ],
	  providers: [],
	  bootstrap: [AppComponent]
	})
	export class AppModule { }


# AppRoutingModule
--------------------------------------------------------------------
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';

	const routes: Routes = [

	  {
	    path: '',
	    loadChildren: () => import('./pages/home/home.module').then(m => m.HomeModule)
	  },

	];

	@NgModule({
	  imports: [RouterModule.forRoot(routes)],
	  exports: [RouterModule]
	})
	export class AppRoutingModule { }

# FirstPageModule - CommonModule
--------------------------------------------------------------------
	import { NgModule } from '@angular/core';
	import { CommonModule } from '@angular/common';

	import { FirstPageRoutingModule } from './first-page-routing.module';
	import { FirstPageComponent } from './first-page.component';


	@NgModule({
	  declarations: [
	    FirstPageComponent
	  ],
	  imports: [
	    CommonModule,
	    FirstPageRoutingModule
	  ]
	})
	export class FirstPageModule { }

# FirstPageRoutingModule - RouterModule
---------------------------------------------------------------------------
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';
	import { FirstPageComponent } from './first-page.component';

	const routes: Routes = [
	  { path: '', component: FirstPageComponent }
	];

	@NgModule({
	  imports: [RouterModule.forChild(routes)],
	  exports: [RouterModule]
	})
	export class FirstPageRoutingModule { }

