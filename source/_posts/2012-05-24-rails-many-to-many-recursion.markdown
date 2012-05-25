---
layout: post
title: "Rails many-to-many recursion"
date: 2012-05-24 15:00
comments: true
categories: rails activerecord migration recursion many
---

googled for a while, determine to roll out my own version.

### The Problem
We have a product, which can acts as material for other products, thus a product can has_many products, at the same time, products are composed by many other products, so a product can also has_many materials(product).

### Solve
Product migration file

    class CreateProducts < ActiveRecord::Migration
      def change
        create_table :products do |t|
          t.string  :name
        end
      end
    end

ProductShip migration file

    class CreateProductShips < ActiveRecord::Migration
      def change
        create_table :product_ships do |t|
          t.integer :product_id
          t.integer :material_id
        end
      end
    end

Model Product

    class Product < ActiveRecord::Base
      has_and_belongs_to_many :products, :class_name => 'Product',
        :join_table => 'product_ships', :foreign_key => :material_id,
        :association_foreign_key => :product_id

      has_and_belongs_to_many :materials, :class_name => 'Product',
        :join_table => 'product_ships', :foreign_key => :product_id,
        :association_foreign_key => :material_id
    end

That's it!! Not that hard isn't it ;)  
but it actually took me 2 hours to come up with this..
